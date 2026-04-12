PwnTillDawn 10.150.150.12

First we need to scan the entire subnetwork to get to the reachable IP address by using ping scan because it is lightweight.

    sudo namp -sn 10.150.150.10/24
![image](https://github.com/0yells/VA-Lab-Work/blob/defa7f5597aabaffa6f3e4c76786bc1af4824eaa/gambo/Screenshot%202026-04-12%20231230.png)

Next, we begin by enumerating the open ports on the target machine using a standard Nmap scan. At this stage, it’s useful to also perform service version detection and run common scripts to gather more detailed information about the target.

-sC (Default Scripts) Runs a set of default NSE (Nmap Scripting Engine) scripts Helps identify: Misconfigurations Basic vulnerabilities Service information

-sV (Service Version Detection) Attempts to determine: Service type (e.g., Apache, vsftpd) Version number

-Pn (No Ping) Skips host discovery (no ICMP ping) Treats the target as alive

     nmap -sC -sV -Pn 10.150.150.12

![image](https://github.com/0yells/VA-Lab-Work/blob/fa72e4e628c7f1334a4f7cc321c63af84b729230/gambo/Screenshot%202026-04-12%20231328.png)

The nmap scan shows us that we have ports 21 (FTP server), 22 (SSH) and 16992 (Intel Archive Management Technology) open. The open port 21 is running vsFTPd 2.0.8, and looks like it allows Anonymous login with user ‘ftp’. A quick google search of the vsftpd 2.0.8 server shows that it is infact quite outdated. Older version such as 2.3.4 seem to have a backdoor which lets a user perform RCE exploits (CVE-2011–2523). So it is likely that these existing exploits also work on this version. Let us check metasploit if we find something.

    msfconsole
    search vsftpd

![image](https://github.com/0yells/VA-Lab-Work/blob/fbf2a5647ec443dd54ddaa24a306ee42a7477c36/gambo/Screenshot%202026-04-12%20231548.png)

As expected, we get a hit on an exploit for the vsftpd 2.3.4 backdoor. Use it by selecting the exploit and setting the RHOST to poral (10.150.150.12) by using ‘show options’, and run the exploit.

    set RHOST 10.150.150.12

![image](https://github.com/0yells/VA-Lab-Work/blob/821e932c0c389384ee5cf4a156800f330e4b9b69/gambo/Screenshot%202026-04-13%20004732.png)

    id
    ls
    cat FLAG!.txt






  

