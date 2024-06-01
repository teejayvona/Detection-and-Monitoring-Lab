# Detection-and-Monitoring-Lab


## Objective

The Detection and Monitoring Lab aimed to simulate and identify cyber threats. It focused on processing and analyzing logs using a Security Information and Event Management (SIEM) system with Splunk and Security Onion through a PFsense CE firewall. The simulated organization utilized an Active Directory Domain, while the attacker employed Kali Linux. This hands-on exercise was designed to deepen understanding of network security, attack methods, and defensive strategies.

### Skills Learned

From this lab work, the following five key lessons were learned:

1. **SIEM Systems and Log Analysis**: Gained practical experience with Security Information and Event Management (SIEM) systems like Splunk and Security Onion for log processing, analysis, and identifying suspicious activities.
2. **Network Security and Firewall Management**: Enhanced understanding of network security principles and firewall management, specifically with PFsense CE, to monitor and protect network traffic.
3. **Active Directory and Attack Methodologies**: Developed skills in setting up and managing an Active Directory Domain and learned various attack methodologies through the use of Kali Linux as an attacking machine.
4. **Defensive Tactics and Incident Response**: Practiced implementing defensive tactics to protect against cyber threats and mitigate potential security breaches, improving incident response capabilities.
5. **Hands-On Cybersecurity Experience**: Acquired valuable hands-on experience in a simulated environment, bridging the gap between theoretical knowledge and real-world application, while fostering collaboration and problem-solving skills.
   
### Tools Used

- Splunk - Utilized as a Security Information and Event Management (SIEM) platform, Splunk facilitates the ingestion and analysis of logs for comprehensive security monitoring and incident detection.
- Security Onion - Utilized as a intrusion detection, network security monitoring, and log management.
- Active Directory - Simulated real-world centralized directory service responsible for overseeing user account management, group memberships, and access permissions throughout the network.
- Pfsense - Used as a firewall and IDS/IPS

## Steps

### Ref 1: Network Diagram

![image](https://github.com/teejayvona/Detection-and-Monitoring-Lab/assets/33003865/1cbfffc4-7cc3-4f61-963f-080c14ebfbaa)


This is the network diagram of what I intend achieving at the end of the project
All these was done using VMware

### Ref 2: Download ISOs

Windows 10: <a href="https://www.microsoft.com/en-us/software-download/windows10">Download Windows 10</a>

Windows 10 Server: <a href="https://www.microsoft.com/en-us/windows-server">Download Windows Server</a>

Ubuntu Server: <a href="https://ubuntu.com/download/server">Download Ubuntu Server</a>

Ubuntu Desktop: <a href="https://ubuntu.com/download/desktop">Download Ubuntu Desktop</a>

Pfsense: <a href="https://www.pfsense.org/download/">Download pfSense</a>

Security Onion: <a href="https://securityonion.net/download">Download Security Onion</a>

Kali Linux: <a href="https://www.kali.org/get-kali/#kali-virtual-machines">Download Kali Linux for VMware</a>

### Ref 4: VMware Network Configuration

Window 10: Vmnet3

Window 10 Server: Vmnet3 

Ubuntu Server (For Splunk): NAT, Vmnet6

Ubuntu Desktop (Security Onion Manager): NAT

Pfsense: NAT, Vmnet2, Vmnet3, Vmnet4, Vmnet5, Vmnet6

Security Onion: NAT, Vmnet4, Vmnet5

Kali Linux: Vmnet2


### Ref 4: Win10 Pro and Win10 Server
I installed Windwos 10 Pro and Win10 Server Desktop edition to use as our taget system and Domain server respectively. 

I then manually added users to the ADD to mimic real users in an organisation. 

Splunk universal forwarder (download from <a href="https://www.splunk.com/en_us/download/splunk-enterprise.html">Download Splunk Enterprise</a>
) and Sysmon (download from <a href="https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon">Download Sysmon</a>
) were install on both systems.


### Ref 5: Kali Linux
Kali was installed on VB from Kali official site and immediately did update on the repositories.


### Ref 6: View Temeletry on Splunk
Login on to Splunk, we notice difference event ID as well as event ID 4625 which for failed login attempt

Going deeper, we notice all the attempts occured within a minute and the ip is from outside our network

### Ref 7: Coming Soon: Installing PFSense, activating IPS and preventing the bruteforce attack

