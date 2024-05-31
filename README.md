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


### Ref 3: SplunkForwarder Installation using a custom inputs.conf

After installing splunk forwarder to listen to my splunk server on 192.168.10.10 on the default port 9997. We need to configure the telemetries to send by opening a Notepad with administrator rights. The code below was then insert and saved on the splunk forwarder local file as "inputs.conf"

[WinEventLog://Application]

index = endpoint

disabled = false

[WinEventLog://Security]

index = endpoint

disabled = false

[WinEventLog://System]

index = endpoint

disabled = false

[WinEventLog://Microsoft-Windows-Sysmon/Operational]

index = endpoint

disabled = false

renderXml = true

source = XmlWinEventLog:Microsoft-Windows-Sysmon/Operational

### Ref 4: Configure Splunk

Log onto 192.168.10.10:8000 with correct details. Go to settings and then indexes to "endpoint" as a new index

Also from setting, select forwarding and listening and add a new port for listening. The listening port is 9997

You might experience a little technical issue like me as below.

![VirtualBox_Windows 10_16_04_2024_21_48_00](https://github.com/teejayvona/Detection-Lab/assets/33003865/48ff714c-7bc9-4139-bccf-9b11e45ef170)

This can be fixed by changing directory on the Splunk server to:

cd /opt/splunk/etc/system/default/

sudo vim server.conf

![VirtualBox_Splunk Server_16_04_2024_22_39_07](https://github.com/teejayvona/Detection-Lab/assets/33003865/7c76c8dc-560f-43ff-a70b-3c7f98c09ebd)

cd /opt/splunk/etc/system/local/
sudo vim server.conf

or better still just paste this on cd /opt/splunk/etc/system/local/

[diskUsage]
minFreespace = 50
pollingFrequency = 100000
pollingTimeFrequency = 10

and that would be sorted

### Ref 4: Win10 Pro and ADD Server Installation
I installed Windwos 10 Pro and ADD Server Desktop edition to use as our taget system and Domain server respectively. 

I then manually added users to the ADD to mimic real users in an organisation. 

Splunk universal forwarder and Sysmon were install on both systems with the addition of ART on Win10 pro only to simulate attack and investigate telemetries.

The users were also given remote desktop rights

### Ref 5: Kali Linux
Kali was installed on VB from Kali official site. We immediately did update on the repositories and eventually installed crowbar which would be used to perform bruteforce attack.

Crowbar comes with a rockyou.txt file contain a bunch of password

By using nano head -n 20 and pointed to password.txt we created a password list for the first 30 to reduce attempt time

We them assume the username 'jadone' has been compromised and type the following for remote desktop brute force attempt

crowbar -b rdp -u jadoe -C password.txt -s 192.168.10.100/32


### Ref 6: View Temeletry on Splunk
Login on to Splunk, we notice difference event ID as well as event ID 4625 which for failed login attempt

Going deeper, we notice all the attempts occured within a minute and the ip is from outside our network

### Ref 7: Coming Soon: Installing PFSense, activating IPS and preventing the bruteforce attack

