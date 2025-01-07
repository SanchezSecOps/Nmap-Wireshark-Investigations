# Nmap & Wireshark for network anomaly investigations

## Overview
This project is meant to be an exercise of what potential malicious activity might look like in a business network environment

Project Highlights
- Topology analysis and vulnerability identification
- Evidence of port scanning found on network
- Recommendations for securing and remediating risks

## Contents
**[Presentation (PDF)](Project1.pdf)** slideshow with more detailed analysis and deep dive into remediations

**Key Screenshots**:
- Nmap topology scan (Screenshots/NmapTopoResult.png)
- Nmap results and identifying the first vulnerability (Screenshots/NmapVulnerabilityID.png)
- PCAP file analysis with Wireshark & display filters (Screenshots/PcapAnalysis-filters.png)
**Supplementary Files**:
  - Network configuration samples.
  - Example ACL rules for mitigating vulnerabilities

 ## Key Findings
 1. **Topology Analysis**:
 - From the nmap results we see after scanning the targetted network that its star topology likely has a central device that lacks advanced routing capabilities
 - Hosts 10.168.27.10 and 10.168.27.15 were flagged by nmap as being high-risk because of multiple open ports and outdated systems

2. **Critical Vulnerabilities**:
- **Unused IP Ranges**: Increased attack surface due to large, unmanaged IP range.
- **Outdated Systems**: Windows Server 2008/2012 and OpenSSH 5.5p1 expose hosts to severe exploits, like EternalBlue.
- **Misconfigured Services**: Anonymous FTP Login, echo services, and insecure HTTP methods like TRACE
- **Port Scanning and SYN Flood**: Activity from host 10.16.80.243 indicates signs of unauthorized recconaissance and denial-of-service attempts

3. **Anomaly Analysis**:
- Port scanning and SYN Flood detected via Wireshark, originating from a single unauthorized host.
- LDAPS query flood suggests potential directory service exploitation attempts.

## Solutions and Mitigation Strategies
The slideshow details at length the recommended actions to secure the network being analyzed
1. **Network Hardening**:
- Deploy intrusion detection and or prevention systems (IDS/IPS) Snort or Suricata may be viable solutions
- Firewalls and network segmentation can help block suspicious traffic post-implementation

2. **Patch Management**:
- Upgrade outdated systems to limit attack vectors and support security patches
- Replace legacy services like SMBv1 with modern protocols.

3. **Authentication Improvements**:
- Enforce strong password policies, enable MFA, and lock unused accounts.

4. **Service configuration**:
- Disable anonymous FTP, echo services, and insecure HTTP methods
- Replace HTTP with HTTPS and secure SSH with updated keys and rate-limiting
  
5. **Proactive Measures**:
- Conduct regular vulnerability scans and penetration tests.
- Monitor directory service traffic for unusual patterns

## Tools and Technologies
- **Nmap**: for network scanning and topology analysis
- **Wireshark**: Packet capture and anomaly detection
- **Zenmap** Nmap GUI to facilitate visualization of scan results

## Lessons Learned
- Importance of maintaining up-to-date systems and configurations.
- Role of proper network segmentation to limit lateral movement within a network
- Value of proactive security measures and training IT personnel with security frameworks and best practices

## Next Steps
- Create a plan of action to implement recommended solutions
- Expand testing, training, and auditing efforts within the organization to improve security awareness and deploy more complex network configurations
- Explore automation to streamline the use of tools and procedures in a secure manner

## About Me
My friends call me Jewel. I'm a security enthusiast for all things digital and physical, and I'm completing a bachelor's in cybersecurity.
I run a small IT and Security business where I consult and support my clients with various services like physical pen-testing and IT security consulting.
Currently, I'm looking to be a part of a larger organization to gain more technical skills and accomplish larger business objectives.
