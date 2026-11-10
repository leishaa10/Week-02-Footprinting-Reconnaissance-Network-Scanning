# Week 02: Footprinting, Reconnaissance & Network Scanning

**Cybersecurity & Ethical Hacking Internship | NETWORKWALKS**

## Project Overview

This repository documents my Week 02 practical activities as part of the Cybersecurity Internship Program at Networkwalks.

The exercises focused on two important stages of penetration testing: **Footprinting and Reconnaissance**, followed by **Network Scanning and Host Discovery**.

The first practical involved gathering publicly available information about the `networkwalks.com` domain using various reconnaissance tools available in Kali Linux.

The second practical focused on discovering active devices within my local network using Zenmap, the graphical interface for Nmap. The activity involved identifying live hosts, examining IP and MAC addresses, and generating a network topology.

These exercises provided practical experience in understanding how cybersecurity professionals gather information, analyze network environments, identify potential security concerns, and document their findings.

## Project Objectives

The primary objectives of this project were to:

- Perform domain footprinting and reconnaissance using Kali Linux tools.
- Gather publicly available domain registration and DNS information.
- Identify website technologies and HTTP response information.
- Detect possible Web Application Firewall technologies.
- Discover active devices within a local network.
- Identify IP and MAC addresses of discovered hosts.
- Examine network device information and vendor details.
- Generate a network topology using Zenmap.
- Document findings and recommend appropriate security improvements.

## Laboratory Environment

| Component | Description |
|---|---|
| Operating Systems | Kali Linux and Windows |
| Reconnaissance Platform | Kali Linux |
| Network Scanning Tool | Zenmap |
| Network Discovery Tool | Nmap |
| Domain Under Assessment | networkwalks.com |
| Network Under Assessment | My own local LAN |
| Training Program | Networkwalks Cybersecurity Internship |
| Program Batch | B084 |
| Modules Completed | W2-PM1 and W2-PM5 |
| Assessment Activities | Footprinting, Reconnaissance and Host Discovery |

## Authorization & Ethical Considerations

All practical activities were performed within an authorized educational environment.

The domain assessment was conducted with permission provided for the training exercise, while network scanning was restricted to my own local network.

All tools and techniques documented in this repository are intended strictly for educational purposes and authorized security assessments.

Unauthorized scanning or testing of systems without appropriate permission is not encouraged.

## Tools and Their Applications

| Tool | Application |
|---|---|
| WHOIS | Retrieve domain registration and name server information. |
| WhatWeb | Identify website technologies and components. |
| Nslookup | Resolve domain names into IP addresses. |
| Curl | Retrieve HTTP response headers. |
| Wafw00f | Identify possible Web Application Firewall technologies. |
| DNSRecon | Gather DNS-related records and infrastructure information. |
| Zenmap | Discover active network hosts and visualize network topology. |
| Windows CMD | Obtain local network configuration and IP information. |

---

## 1. Footprinting and Reconnaissance

### Overview

The first phase involved gathering publicly available information about the `networkwalks.com` domain using six reconnaissance tools available in Kali Linux.

### 1.1 WHOIS – Domain Information Gathering

WHOIS was used to retrieve publicly available domain registration information and examine the domain's name server details.

This helped understand the domain's registration and DNS infrastructure.

### 1.2 WhatWeb – Website Technology Identification

WhatWeb was used to identify technologies and components associated with the target website.

The results identified:

- WordPress 7.0.4
- WP Download Manager 3.3.58

### 1.3 Nslookup – Domain Name Resolution

Nslookup was used to resolve the domain name into its corresponding IP address.

**Observed IP Address:** `192.232.216.135`

### 1.4 Curl – HTTP Header Inspection

Curl was executed using the `-I` option to retrieve HTTP response headers.

The output revealed additional technical information about the website, including the WordPress REST API endpoint:

`/wp-json/`

### 1.5 Wafw00f – Web Application Firewall Identification

Wafw00f was used to investigate whether the target website was protected by a Web Application Firewall.

**Identified WAF:** ModSecurity (SpiderLabs)

### 1.6 DNSRecon – DNS Record Enumeration

DNSRecon was used to gather additional information about the domain's DNS configuration.

The assessment covered:

- Name Servers (NS)
- Mail Servers (MX)
- SPF and TXT Records
- Service Records (SRV)
- DNS infrastructure information

---

## 2. Network Scanning and Host Discovery with Zenmap

### Overview

The second practical focused on discovering active devices within my local network using Zenmap.

The objective was to identify live hosts, collect their IP and MAC address information, examine vendor details, and generate a network topology.

### 2.1 Identifying the Local Network

Windows Command Prompt was used to examine the local network configuration before performing the scan.

The network subnet used for the practical was:

`192.168.0.0/24`

### 2.2 Host Discovery using Zenmap

Zenmap was used to perform a Ping Scan across the local network.

**Command used:**

```bash
nmap -sn 192.168.0.0/24
```

The scan examined 256 IP addresses and identified **8 active hosts** within the network.

### 2.3 Active Hosts Identified

The following IP addresses were identified as active during the scan:

| No. | IP Address |
|---|---|
| 1 | 192.168.0.1 |
| 2 | 192.168.0.100 |
| 3 | 192.168.0.102 |
| 4 | 192.168.0.103 |
| 5 | 192.168.0.104 |
| 6 | 192.168.0.108 |
| 7 | 192.168.0.109 |
| 8 | 192.168.0.111 |

### 2.4 MAC Address and Vendor Identification

The scan returned MAC address information for seven of the eight discovered hosts.

Vendor identification results included:

- **192.168.0.1:** TP-Link Technologies
- **192.168.0.100:** Amazon Technologies

The remaining identified devices displayed unknown vendor information.

The host `192.168.0.103` did not return a MAC address, possibly because it was the machine performing the scan.

### 2.5 Network Topology Generation

After completing host discovery, the Topology section in Zenmap was used to visualize the discovered network devices.

The topology view was configured with the legend enabled and exported as a PDF file.

This provided a graphical representation of the discovered network environment.

---

## 3. Findings and Risk Assessment

The practical exercises revealed several observations relevant to cybersecurity assessment.

| No. | Observation | Potential Security Implication | Risk Level |
|---|---|---|---|
| 1 | Website technologies identified through WhatWeb. | Public technology information may assist further software assessment. | Medium |
| 2 | Domain resolved to an identifiable IP address. | Provides information about the web service's network location. | Low |
| 3 | HTTP headers and `/wp-json/` endpoint were observable. | May assist further application enumeration. | Low |
| 4 | ModSecurity identified through Wafw00f. | Reveals information about the website's security architecture. | Low |
| 5 | DNS records collected using DNSRecon. | DNS information may help build an infrastructure profile. | Medium |
| 6 | Eight active hosts discovered on the local network. | Unknown or unauthorized devices should be investigated. | Medium |
| 7 | MAC addresses and vendor information identified. | Helps understand connected devices and their network identities. | Informational |

**Risk Assessment Note:**

The findings represent observations from footprinting and network scanning activities, not confirmed vulnerabilities.

No exploitation or vulnerability validation was performed during these practical exercises.

## 4. Security Recommendations

Based on the observations, the following security improvements are recommended:

1. **Review Publicly Exposed Technology Information:** Regularly assess publicly visible information about website technologies, CMS platforms, and plugins.

2. **Maintain Updated Software:** Keep web applications, plugins, and supporting technologies updated.

3. **Strengthen HTTP Security Configuration:** Review HTTP response headers and apply appropriate security configurations.

4. **Review DNS Configurations:** Ensure DNS records are accurate and expose only necessary information.

5. **Configure and Monitor WAF:** Maintain appropriate Web Application Firewall configurations and security rules.

6. **Perform Regular Network Discovery:** Periodically scan authorized networks to identify active devices.

7. **Investigate Unknown Devices:** Verify unfamiliar devices discovered during network scanning.

8. **Maintain Network Documentation:** Keep IP address assignments and network topology documentation updated.

9. **Ensure Authorized Security Testing:** Conduct reconnaissance and network scanning only within an approved scope.

## 5. Key Learning Outcomes

The Week 02 practical activities helped strengthen my understanding of:

- **Footprinting and Reconnaissance:** Gathering publicly available information about a target domain.
- **Web Technology Identification:** Identifying website technologies using WhatWeb.
- **DNS Analysis:** Understanding domain resolution and DNS records using Nslookup and DNSRecon.
- **HTTP Response Analysis:** Examining HTTP headers using Curl.
- **WAF Identification:** Understanding how Web Application Firewalls can be identified using Wafw00f.
- **Network Discovery:** Identifying active devices within a local network using Zenmap.
- **MAC Address Identification:** Understanding how MAC addresses and vendor information help identify network devices.
- **Network Topology:** Visualizing connected devices through Zenmap.
- **Security Documentation:** Recording observations and assessing potential security implications.
- **Ethical Security Testing:** Understanding the importance of authorization and responsible cybersecurity practices.

## 6. Conclusion

Week 02 provided practical exposure to footprinting, reconnaissance, and network scanning as part of my Cybersecurity and Ethical Hacking Internship at Networkwalks.

Using WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon, I explored different techniques for gathering publicly available domain information and understanding website technologies and DNS infrastructure.

The Zenmap practical helped me discover eight active hosts within my local network, examine their IP and MAC address information, identify available vendor details, and generate a network topology.

These exercises improved my understanding of how information gathering and network discovery contribute to the initial stages of penetration testing.

Overall, the practical activities strengthened my technical knowledge, observation skills, and ability to document cybersecurity findings responsibly.

## 7. Evidence and Documentation

Screenshots and supporting materials from the practical exercises are included in this repository as evidence of the activities performed.

**Evidence includes:**

- WHOIS domain information
  <img width="957" height="933" alt="image" src="https://github.com/user-attachments/assets/b831c6bf-bfd3-4d82-b866-4cf2ce4f911e" />

- WhatWeb technology identification results
  <img width="947" height="971" alt="image" src="https://github.com/user-attachments/assets/9479ec68-3a32-41f7-981f-3fa9eb5090e3" />

- Nslookup domain resolution output
  <img width="960" height="1011" alt="image" src="https://github.com/user-attachments/assets/b292a49d-409e-4270-a373-d8a653dd734f" />

- Curl HTTP response headers
  <img width="957" height="975" alt="image" src="https://github.com/user-attachments/assets/5909a6de-0035-4303-b4f9-6fe49809a7b5" />

- Wafw00f WAF identification results
  <img width="956" height="762" alt="image" src="https://github.com/user-attachments/assets/3e0e8be3-c2d0-40c9-8a62-044b4ccb0181" />

- DNSRecon enumeration results
  <img width="952" height="873" alt="image" src="https://github.com/user-attachments/assets/47a1b5b0-1ebb-45fb-bd95-81e7721ec950" />

- Zenmap host discovery results and Active host IP and MAC address information
  <img width="1911" height="735" alt="Screenshot 2026-11-10 191905" src="https://github.com/user-attachments/assets/9c8433b9-a584-40fe-8ca2-82a4ab2ecd5b" />
  
- Network topology
<img width="1917" height="1025" alt="Screenshot 2026-11-10 192013" src="https://github.com/user-attachments/assets/088a1ed9-f9cc-49a6-865e-eaaf1c86856f" />

## Author

**Name:** Leisha Santoshkumar  
**Role:** Cybersecurity Professional Intern  
**Program:** Networkwalks Cybersecurity Internship  
**Batch:** B084  
**Project:** Week 02 – Footprinting & Network Scanning

