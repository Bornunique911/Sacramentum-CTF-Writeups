```console
# Nmap 7.91 scan initiated Sat Oct  2 20:29:18 2021 as: nmap -vvv -p 21,80 -A -Pn -oN pallet_city_nmap 10.10.100.240
Nmap scan report for 10.10.100.240 (10.10.100.240)
Host is up, received user-set (0.20s latency).
Scanned at 2021-10-02 20:29:19 IST for 56s

PORT   STATE SERVICE REASON  VERSION
21/tcp open  ftp     syn-ack vsftpd 2.0.8 or later
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
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
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
80/tcp open  http    syn-ack Apache httpd 2.4.18 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
| http-robots.txt: 2 disallowed entries 
|_/profslab/ /profslab/flag
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Pallet City

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Oct  2 20:30:15 2021 -- 1 IP address (1 host up) scanned in 57.19 seconds
```
