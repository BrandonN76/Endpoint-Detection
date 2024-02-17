## EDR Detection Lab

**Description:**  
In this lab, I will simulate a cybersecurity scenario focusing on a Windows system being targeted by a custom Command and Control (C2) payload. My objective is to successfully set up the attack and monitor it using the Endpoint Detection and Response (EDR) solution called LimaCharlie. The goal of this lab is to gain a deeper understanding of both offensive and defensive aspects of cybersecurity, exploring tactics used by attackers and the effectiveness of defensive measures in detecting and responding to threats.

**Virtual Machines in VMware:**  
- Windows VM (Victim)  
- Ubuntu Server (Attacker)

**Programs used:**  
- Sysmon  
- LimaCharlie (EDR)  
- Sliver (Used to create and launch the C2 payload)

**Victim Setup:**  
Deployed the Windows Virtual Machine in VMware and disabled the security features in Windows settings and registry. Installed the necessary programs to detect an attack on the system (Sysmon and EDR).

(LimaCharlie EDR)
<img src="https://i.imgur.com/1seH1Q3.png">

**Attacker Setup:**  
Deployed a Ubuntu Virtual Machine. Installed the necessary programs to conduct the attack (Sliver). Created a C2 payload in Sliver and sent it to the victim.
<img src="https://i.imgur.com/xBSkTT6.png">
<img src="https://i.imgur.com/et0vlXB.png">

**Execution:**  
The C2 payload was executed, and a session was started with the attacker and the victim. The attacker gathered system information and then dumped the lsass.exe to extract sensitive information.

(Attack with Sliver)
<img src="https://i.imgur.com/nlDTbaB.png">
<img src="https://i.imgur.com/kKMw9PO.png">

**Detection:**  
EDR solution detected the C2 payload and its attempts to run reconnaissance by running netstat on the system, and its access to a sensitive file called lsass.exe. I created a custom detection and response rule to detect when attackers access the lsass.exe file since it is commonly attacked.

(EDR Tool detected a network connection with WEIRD_LIPSTICK.exe)
<img src="https://i.imgur.com/laL0iun.png">

(More information on the strange connection.)
<img src="https://i.imgur.com/uSRjYnU.png">

(EDR detects tampering with a sensitive process.)
<img src="https://i.imgur.com/bUObs3w.png">
