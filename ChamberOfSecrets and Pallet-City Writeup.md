### Chambers Of Secrets :

For nmap results check `nmap.md` file. For the first flag check `Sword.txt` and for the rest flags `flags.txt` .

---

### First Flag : 

As the ftp server port was open, I went there to enumerate it and I got the `passwd.txt` file and also one directory named `.GodricGryffindor` directory. 
When I visited `.GodricGryffindor` directory I got `Sword.txt` file which is our first flag for the challenge. 

---
### Flag 1 :
```console
Ch4mb3r0fS3cr3ts{Al4rt3_A5c3nd@r3}
```
---

When I did done further enumeration I got the `...` directory and in that directory I got the other `passwd.txt` file which I guess was a password for the user or something because looking at the nmap results we came to know that the ssh port is also open.

---
### Second Flag : 

As we observe from our nmap results we come to know about the samba is running on the machine. 
I enumerated both the ports `139` and `445` respectively but I didn't find any interesting share using `smbclient`. 
But my mind blinked and came to know that we have `two` `passwd.txt` files. 
So I checked both the files wherein in one file (`passwd_1.txt`) there was a leet language string and in the other file(`passwd.txt`) there was a `base64 string`. 
So I used `CyberChef` for decoding the `base64 string` and for other file I used my mind skill for decoding the string and I got this as an output which is as follows:

`Of course it's happening inside your head, Harry. Why should that mean that it's not real?`

`1_4m_Th3_Ch0s3n_0n3` = `I_am_The_Chosen_One`

So from the above text, we can get an idea that `Harry` can be a ssh user. 
So I tried doing ssh with `Harry` as a user and `1_4m_Th3_Ch0s3n_0n3` as a password but there was no luck there. 
But as I was sure that it was a leet language in the passwd.txt file so I tried to visit the leet generator website for generating Harry in the leet language string. 
So I tried many attempts for and at last I tried to typing this `h4rry` as a user and `1_4m_Th3_Ch0s3n_0n3` as the password and boom we are logged in the ssh session.
But what about the flag?

The main deal is the second flag. 
So I tried enumerating the file system and in the home directory of the user `h4rry` we got one interesting directory called `GodricHollow`. 
So I visited that directory and there I found one `Seeker.txt` file and guess what it is a second flag for the challenge. 

---
### Flag 2 :
```console
Ch4mb3r0fS3cr3ts{D3v1Ls_5n4R3}
```
---

### Third Flag : 
But what next after getting `flag2` should I have to pwned the machine? 

Yes, I have pwned the machine and I have to grab the `flag3`.

So it's time for privilege escalation :

So the simple step for privilege escalation is to type 
```console
sudo -l
``` 
to see which binary or file or command is vulnerable to root user. But sadly it didn't work because the h4rry was not in the sudoers list.So what to do next???

We can type `id` or else we can check the sudo version as it is now common after the `Baron Samedit sudo version exploit`. 
So I checked the sudo version and it was vulnerable and if I typed `id` it showed me this as output:-

```console
uid=1001(h4rry) gid=1001(h4rry) groups=1001(h4rry),130(lxd)
```
 
So after observing the output of `id` command, the user `h4rry` is included in the `lxd group`. 
So we can exploit it by building a `alpine image`. 
For the exploitation of root user, refer this website mentioned below:

https://www.hackingarticles.in/lxd-privilege-escalation/
 
### Flag 3 :
```console
Ch4mb3r0fS3cr3ts{1_4m_L0rd_V0ld3m0rt}
```


### References For :

Privilege Escalation : https://www.hackingarticles.in/lxd-privilege-escalation/

Base64 string file : passwd.txt

password file :  passwd_1.txt 

nmap scan results : nmap.md 

Flag1 : Sword.txt 

Flag2 and Flag3 : flags.txt 
                  

----------------------------------------------------------------------------------------------------------------------------------------------------------------

### Pallet-City

For nmap results, refer `pallet_city_nmap.md` file.

*Ports Open in the beginning :* *21,80*

So I visited ftp server first as a anonymous user by referring the nmap results and I got the `.ssh` file in the file system which is in the `...`directory as it was a similar practice in the `ChamberOfSecrets` challenge.
In the `.ssh` file the pokemon name called `golisopod` was mentioned in the leet language.

---

### First Flag :

I enumerated `port 80`, and I find the `two disallowed entries` on the website in the `robots.txt` file and a key which was unknown where to use. 
But I enumerated further the disallowed entries which were `profslab directory` and `/profslab/flag` file. 
So I also noticed the cookie value by inspecting the element and guess what it was `jwt token`. 
So I copied that cookie value in the website called `https://jwt.io` and there I come to know that it requires a secret key for verifying the signature and also I noticed the payload `name` which has `User` as a value. 
So I used the key which I found earlier as a secret key and I changed the payload value to `Ash Ketchum` for the payload `name` which can be found on the `main(home) page` but it won't work so I tried removing spaces between `Ash Ketchum` which ultimately looks like `AshKetchum` and so I got the new jwt token which is as under :

`eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiQXNoS2V0Y2h1bSJ9.12ECr1DzjsX9F2urJNnr4SVfoQEMwp23HLU95sZt5dY`

Replacing the cookie value gives us the `profslab/flag` page as this as an output :-
```console
You are here
The flag is : pallet-city{g0TT@_c@Tch_3m_@Ll}
Me, giveup? No Wayyy!
The hint is https://bit.ly/hintshere
```
### Flag 1 : 
```console
pallet-city{g0TT@_c@Tch_3m_@Ll}
```

So, finally got our first flag. 
Let's move further for the remaining flags.

---

### Second Flag :

For the second flag, we got one link as a hint and while visiting that link, it was basically a `mega file` which consist of `hints.zip` file. 
So let's download it first and unzip it but it requires password which is not known to us. 
So there is one tool called `fcrackzip` which can crack the zip file password by specifying the wordlist. 
So, I crack the zip file password via `fcrackzip tool` and the resultant password was `Charizard-Pokemon` and boom we got access to two files which are `img.jpg` and `hint.docx`.
The first file was simply a image file and other one was a docx file but is it really a docx file I suspect because by using file command it showed me pcapng file as an output.
So my suspect turns into reality that it is not a docx file but it merely a `pcapng file`.
When I analyse that file, I came to know about the `three ports(11701,11702,11703)` which are knocked by `one single ip(192.168.1.44)`. 
So, I used the `knocking tool(knock tool)` which can knocked the `three ports` for us. 
So, I used that tool for knocking and when I tried doing nmap again it showed me `ssh port(22)` open. 
So, I tried to ssh with the user `ashketchum` and `g0L150p0D` as a password and boom I was logged in the ssh session. 
And I got the second flag from the home directory of the user `ashketchum`.So after getting the second flag, now it's time for privilege escalation.

### Flag 2 :
```console
pallet_city{YouMightBeAshNowButAreYouWorthyEnoughOfMewtwo?}
```
---
### Third Flag :

I tried 
```console
sudo -l
```
but there was no success.

So, I used find command as under:-

```console
find / -perm -u=s -type f 2>/dev/null
```

and I got `one binary file` in the `/var/log` path.

### Path Hijacking vuln :

1) Make a new file called cat in the tmp directory.
```console
mkdir /tmp/cat
```
Contents of `/tmp/cat` file is as under :
```console
chmod +s /bin/bash
```

2) And make it executable file with following command :
```console
chmod +x /tmp/cat
```
3) To hijack the path variable we need to export the tmp directory path as 
```console
export PATH=/tmp:$PATH
```
4) After doing that navigate to `/var/log` and just `execute the binary` thereafter and after running the binary type this command 
```console
/bin/bash -p
```  
to get the root user.

### Flag 3 :
```console
pallet_city{MeetMewTwoatCeruleanCave}
```

---
### References For : 

https://jwt.io/                 

https://bit.ly/hintshere

https://www.wireshark.org/

https://github.com/jvinet/knock/

Nmap results :- pallet_city_nmap.md

Flag1, Flag2, Flag3 :- flags.txt

---

### Important Notes :

Common things to note in both the machines is ftp server has a `anonymous login` and also in the file system we have the directory which starts from `three dots` that's quite rare in the actual file system.
Also many were facing issues for submitting flags, but there were this characters ```​​``` in the beginning of the flag characters and at the end of the curly braces.

