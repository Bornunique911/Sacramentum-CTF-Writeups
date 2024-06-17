```console
# Nmap 7.91 scan initiated Sat Oct  2 17:42:32 2021 as: nmap -vvv -p 445,139,22,21 -A -Pn -oN nmap 10.10.184.82
Nmap scan report for 10.10.184.82 (10.10.184.82)
Host is up, received user-set (0.26s latency).
Scanned at 2021-10-02 17:42:32 IST for 54s

PORT    STATE SERVICE     REASON  VERSION
21/tcp  open  ftp         syn-ack vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.8.90.38
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp  open  ssh         syn-ack OpenSSH 7.2p2 Ubuntu 4ubuntu2.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 8b:49:c6:43:76:5d:b7:43:31:26:e2:a2:b9:71:5e:6a (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDfl8TVv3fgn3l4vwn6HiDF+Cntm52CQHJA97dN9dT340oo2mp4J5CgrZxAt2wBznmtokQ8NofXEBrqVzdQmletRfMVKRo03fI/XpavTD3/j/528E1M3xQkoVAAp6bemQKLzWbn5/aRbALMzXRHi83t9Ez1/QWcP86ZS073JqfOHz7vk6tC8s2J4JfL0R7d5XseB6Jh3JiYH8+rU9Y45GMV2W44+BrEPboBKj5rmudiKXNJakxPw/391bXJVF27Mh9jQzWbNqm2kr95aA+tV8nvH/fa2ApCYYZHtRPI3AOXLxTDzj2LEzJZVB3hS3X9IXHS3nQ08D/dS2SfbfCurG9f
|   256 52:68:77:5e:a1:d0:14:9a:7d:61:72:06:72:72:6b:17 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBMR+O3trcZKDzNBn6q/XLyRzCRW9RtYNjz9jiExgFDwC5xarixR3Y7fmGeOvqk7/A2CgMMWLQKHpWU3/DM18CWI=
|   256 05:02:cc:e3:fb:68:37:d4:00:94:bc:6c:e4:39:71:af (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDSbZksApE+Td4Dkb3VMJzv6tfn2iBkVI2Og1H+biC0I
139/tcp open  netbios-ssn syn-ack Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn syn-ack Samba smbd 4.3.11-Ubuntu (workgroup: WORKGROUP)
Service Info: Host: CHAMBEROFSECRETS; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: 2h20m47s, deviation: 4h02m33s, median: 45s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 25042/tcp): CLEAN (Timeout)
|   Check 2 (port 28542/tcp): CLEAN (Timeout)
|   Check 3 (port 59269/udp): CLEAN (Timeout)
|   Check 4 (port 39355/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.3.11-Ubuntu)
|   Computer name: \x00
|   NetBIOS computer name: CHAMBEROFSECRETS\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2021-10-02T05:13:37-07:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-10-02T12:13:35
|_  start_date: N/A

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Oct  2 17:43:26 2021 -- 1 IP address (1 host up) scanned in 54.50 seconds
```
