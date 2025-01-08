# TryHackMe AvatarCTF — Walkthrough by Aman Chauhan

![Aman Chauhan](https://miro.medium.com/v2/da:true/resize:fill:88:88/0*CxDs-Ddcy-01hGxi)

**AvatarCTF** is a medium-level Capture the Flag (CTF) challenge on TryHackMe. It tests your skills in scanning, enumeration, steganography, password cracking, and privilege escalation.

**Note**: This is the first room I’ve created on TryHackMe, so I hope you enjoy solving it!

First of all deploy the machine and start nmap scan with the following command:

```bash
nmap -A -Pn -v IP
```
![Key Generation](images/screenshot1.png)
### Nmap Scan Results

The `nmap` scan shows two open ports:

- **Port 22 (SSH)**
- **Port 8001 (HTTP)**

Port 8001 is hosting an Apache2 web server, so let’s check it out.

![Key Generation](images/screenshot2.png)

The page only displays the default Apache2 welcome screen. Next, let's look at `robots.txt`.

![Key Generation](images/screenshot3.png)

The `robots.txt` file contains a Base64-encoded string. Decode it using:

```bash
echo "base64 string" | base64 -d
```
![Key Generation](images/screenshot4.png)

After decoding, it’s just a rabbit hole. Time to keep enumerating!

Start the directory using gobuster with the following command.

```bash
gobuster dir -u http://IP:8001/ -w /usr/share/wordlists/rockyou.txt
```
![Key Generation](images/screenshot5.png)

Using `gobuster`, we discover a `/web2` directory. Let’s explore it.

![Key Generation](images/screenshot6.png)


