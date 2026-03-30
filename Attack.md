# This document shows the steps of a brute-force attack in a TEST environment against an Azure Virtual Machine using Netcrack and rockyou.txt
## Adversary device: my own PC running Windows 10 Pro.
## Attacked device: an Azure Virtual Machine running Linux, in my own Azure subscription.
## Attack method: brute-force the administrator account password using Netcrack and rockyou.txt
## Exploited vulnerabilities: left-open SSH port and weak password
## MITRE ATT&CK tactic used: TA0006: Credentials Access
## Attack steps:
- I created an Azure VM with Linux. Defender for Cloud (Servers) in enabled in my subscription. In the network settings, I left the SSH port 22 open for inbound traffic. I also created a weak password for the administrator account.<img width="1862" height="826" alt="ssh_left_open" src="https://github.com/user-attachments/assets/c5f6520f-a107-43a3-98cb-3fdda5c9c08b" />
- I used the nmap command on my PC to check the open ports of the VM (using its public IP address). I found the SSH port open.<img width="627" height="206" alt="nmap_port_check" src="https://github.com/user-attachments/assets/f483b6ac-46ad-40d2-8171-0f48c4f7341b" />
- I obtained the rockyou.txt file from weakpass.com. It is a directory holding a number of password lists that can be used by multiple tools when attempting to guess credentials for a given targetted service.
- I executed the ncrack command, using: SSH protocol, the administrator username, the public IP of the VM and rockyou.txt file.<img width="876" height="283" alt="ncrack_command" src="https://github.com/user-attachments/assets/928b69ea-9161-4939-8aa5-bb4508c0a62e" />
- I did not let the attack go though, the purpose was only to set off the alert in Defender for Cloud - please see "Response" file.
