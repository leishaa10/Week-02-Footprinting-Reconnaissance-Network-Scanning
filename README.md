
# Week 02 – Footprinting, Reconnaissance & Network Scanning

## Cybersecurity Internship | Networkwalks

This repository contains the practical work completed during Week 02 of my Cybersecurity Internship at Networkwalks.

The activities covered two practical modules:

- **W2-PM1:** Footprinting and Reconnaissance using Kali Linux tools.
- **W2-PM5:** Network Scanning and Network Discovery using Zenmap.

The practicals focused on gathering publicly available information, identifying website technologies, enumerating DNS records, discovering active network hosts, and visualising network topology.

---

## Objectives

- Understand the fundamentals of footprinting and reconnaissance.
- Collect publicly available domain information.
- Identify website technologies and frameworks.
- Perform DNS lookup and DNS enumeration.
- Inspect HTTP response headers.
- Detect Web Application Firewall technology.
- Discover active devices on a local network.
- Identify IP and MAC addresses.
- Generate a network topology using Zenmap.

---

## Lab Environment

| Parameter | Details |
|---|---|
| Internship | Networkwalks |
| Program/Batch | B084-Networkwalks |
| Week | 02 |
| Operating System | Kali Linux and Windows |
| Target Domain | networkwalks.com |
| Target IP | 192.232.216.135 |
| Local Network | 192.168.0.0/24 |
| Scan Date | 10 November 2026 |

---

## Authorization and Scope

All activities were performed on systems and networks for which permission was secured or which I owned.

The footprinting activity was performed against the assigned Networkwalks domain with written permission. Network scanning was performed on my own local LAN.

These exercises were conducted for educational and research purposes. No exploitation or unauthorized access was performed.

---

# Practical 1 – Footprinting and Reconnaissance (W2-PM1)

Six Kali Linux tools were used to gather information about the target domain.

## 1. WHOIS – Domain Information Gathering

**Objective:** To collect publicly available domain registration information.

**Tool:** WHOIS

**Information examined:**
- Domain registration details
- Registrar information
- Registration and expiry information
- Name servers
- Hosting-related information

**Observation:** WHOIS provided publicly available registration and name server information about the target domain.

**Security significance:** Domain registration information can help security professionals understand domain ownership and hosting infrastructure.

## 2. WhatWeb – Website Technology Identification

**Objective:** To identify technologies and frameworks used by the target website.

**Tool:** WhatWeb

**Target:** networkwalks.com

**Observations recorded in the report:**
- WordPress 7.0.4
- WP Download Manager 3.3.58

**Security significance:** Technology fingerprinting helps identify the software used by a website and determine which components may require security review.

## 3. Nslookup – DNS Lookup

**Objective:** To resolve the target domain into its corresponding IP address.

**Tool:** Nslookup

**Observation:**

```text
Domain: networkwalks.com
Resolved IP: 192.232.216.135
```

**Security significance:** DNS lookup helps identify the IP address associated with a domain and provides useful information during reconnaissance.

## 4. cURL – HTTP Response Analysis

**Objective:** To inspect HTTP response headers returned by the website.

**Tool:** cURL

**Command:**

```bash
curl -I https://networkwalks.com
```

**Observations:**
- HTTP response headers were retrieved.
- Additional web application information was observed.
- WordPress REST API endpoint identified: `/wp-json/`

**Security significance:** HTTP response analysis helps identify information exposed by a web server and supports further security assessment.

## 5. Wafw00f – Web Application Firewall Detection

**Objective:** To identify whether a Web Application Firewall protects the website.

**Tool:** Wafw00f

**Observation:**

```text
Detected WAF: ModSecurity (SpiderLabs)
```

**Security significance:** Identifying WAF technology provides information about the defensive mechanisms used by a website.

## 6. DNSRecon – DNS Enumeration

**Objective:** To enumerate DNS records associated with the target domain.

**Tool:** DNSRecon

**Command:**

```bash
dnsrecon -d networkwalks.com
```

**Records examined:**
- SOA records
- NS records
- MX records
- A records
- TXT records
- SPF information
- SRV records

**Key observations:**
- Two name servers were identified.
- Mail server information was discovered.
- The domain resolved to 192.232.216.135.
- Google site verification TXT information was identified.
- SPF configuration was discovered.
- Email autodiscovery SRV records were identified.
- No answer was received for the DNSSEC query.

**Security significance:** DNS enumeration helps understand domain infrastructure, mail configuration, and publicly exposed DNS information.

---

## Evidence – Footprinting & Reconnaissance

### 1. WHOIS – Domain Information
<img width="957" height="933" alt="whois" src="https://github.com/user-attachments/assets/84420a08-2ca2-40ad-a276-914adff31033" />


### 2. WhatWeb – Technology Identification
<img width="947" height="971" alt="whatweb" src="https://github.com/user-attachments/assets/d6bdd3df-0831-494f-86c2-349e82c56635" />


### 3. Nslookup – DNS Lookup
<img width="960" height="1011" alt="nslookup" src="https://github.com/user-attachments/assets/61be44e0-4247-42a7-af47-53894ff2de9e" />


### 4. cURL – HTTP Response
<img width="957" height="975" alt="curl -I " src="https://github.com/user-attachments/assets/c315f86b-0a91-40c0-841f-0b231be193c3" />


### 5. Wafw00f – WAF Detection
<img width="905" height="526" alt="waafw00f" src="https://github.com/user-attachments/assets/235a7832-348e-491a-ad95-ecbc9472ef79" />


### 6. DNSRecon – DNS Enumeration
<img width="952" height="873" alt="dnsrecon" src="https://github.com/user-attachments/assets/5e6fac93-74e5-461e-947f-809a43353bac" />



# Practical 2 – Network Scanning Using Zenmap (W2-PM5)

## Objective

To identify the local network configuration, discover active hosts, collect IP and MAC address information, and generate a network topology.

**Tools Used:**
- Windows Command Prompt
- Nmap
- Zenmap

## Network Details

| Parameter | Result |
|---|---|
| Network Subnet | 192.168.0.0/24 |
| Scan Type | Ping Scan |
| Total IP Addresses Scanned | 256 |
| Active Hosts Found | 8 |
| Scan Duration | 18.31 seconds |

## Command Used

```bash
nmap -sn 192.168.0.0/24
```

**Command explanation:**
- `nmap` – Network exploration and security auditing tool.
- `-sn` – Performs host discovery without a port scan.
- `192.168.0.0/24` – Specifies the local network range.

## Active Hosts Discovered

| No. | IP Address | Observation |
|---|---|---|
| 1 | 192.168.0.1 | TP-Link Technologies |
| 2 | 192.168.0.100 | Amazon Technologies |
| 3 | 192.168.0.102 | Unknown vendor |
| 4 | 192.168.0.103 | No MAC address displayed |
| 5 | 192.168.0.104 | Unknown vendor |
| 6 | 192.168.0.108 | Unknown vendor |
| 7 | 192.168.0.109 | Unknown vendor |
| 8 | 192.168.0.111 | Unknown vendor |

**Additional observations:**
- Eight active hosts were discovered.
- Seven hosts returned MAC addresses.
- Two devices were matched to vendors.
- The remaining five MAC addresses showed unknown vendors.
- The host at 192.168.0.103 did not return a MAC address and was suspected to be the scanning machine.

## Network Topology

After completing the scan, Zenmap's Topology section was used to visualise the discovered network.

The legend was enabled, and the network topology was exported as a PDF.

**Importance of network mapping:**
- Helps identify active devices.
- Provides an overview of network structure.
- Helps maintain a device inventory.
- Supports network monitoring and security assessment.

---

## Evidence – Network Scanning

### 1. Nmap / Zenmap Host Discovery
<img width="1911" height="735" alt="ip and mac addresses" src="https://github.com/user-attachments/assets/efec22b9-21b6-44fa-bcdc-e4b679fa2968" />


### 2. Zenmap Network Topology
<img width="1917" height="1025" alt="topology" src="https://github.com/user-attachments/assets/3cbef059-345e-4c76-962a-1772b12c478a" />


# Consolidated Findings

| Tool | Purpose | Key Observation |
|---|---|---|
| WHOIS | Domain information gathering | Registration and name server information |
| WhatWeb | Technology fingerprinting | WordPress and WP Download Manager |
| Nslookup | DNS lookup | 192.232.216.135 |
| cURL | HTTP response analysis | `/wp-json/` endpoint observed |
| Wafw00f | WAF detection | ModSecurity (SpiderLabs) |
| DNSRecon | DNS enumeration | NS, SOA, MX, A, TXT, SPF and SRV information |
| Nmap | Network discovery | 8 active hosts |
| Zenmap | Network visualisation | Network topology generated |

---

# Risk Analysis

The practical exercises revealed information that could be useful during reconnaissance.

| Finding | Potential Impact | Risk Level |
|---|---|---|
| Website technology information exposed | Helps identify software requiring security review | Medium |
| Server IP address identifiable | Provides information about hosting infrastructure | Low |
| HTTP technical information exposed | May assist further technology fingerprinting | Low |
| WAF technology identifiable | Reveals information about security architecture | Low |
| DNS infrastructure information exposed | Helps build an infrastructure profile | Medium |
| Multiple live hosts visible | Unexpected devices may require investigation | Medium |

**Note:** These are observations from information gathering and host discovery, not confirmed vulnerabilities. No exploitation or vulnerability validation was performed.

---

# Security Recommendations

1. **Review publicly exposed technology information:** Regularly review what information about web technologies and plugins is publicly visible.
2. **Keep software updated:** Update CMS platforms, plugins, and other website components.
3. **Review HTTP headers:** Check whether unnecessary technical information is exposed.
4. **Review DNS records:** Ensure only required DNS information and services are publicly exposed.
5. **Configure and monitor the WAF:** Keep ModSecurity enabled and regularly review its configuration.
6. **Perform regular network discovery:** Periodically identify active devices on internal networks.
7. **Investigate unknown devices:** Verify unexpected devices discovered during network scanning.
8. **Maintain network documentation:** Keep network topology and device information updated.
9. **Perform authorised security testing:** Conduct reconnaissance and scanning only within the approved scope.

---

# Learning Outcomes

Through these practical exercises, I gained hands-on experience in:

- Domain footprinting and reconnaissance.
- WHOIS information gathering.
- Website technology identification using WhatWeb.
- DNS resolution using Nslookup.
- HTTP response analysis using cURL.
- WAF detection using Wafw00f.
- DNS enumeration using DNSRecon.
- Network discovery using Nmap.
- Network topology visualisation using Zenmap.
- Documenting technical findings and potential security risks.

---

# Conclusion

Week 02 provided practical exposure to footprinting, reconnaissance, DNS enumeration, website technology identification, and network scanning.

Using multiple Kali Linux tools helped me understand how publicly available information can be collected and analysed during the initial stages of a cybersecurity assessment.

The Zenmap practical further helped me understand local network discovery, active host identification, and network topology visualisation.

These exercises strengthened my understanding of information gathering, network discovery, and the importance of performing security assessments within an authorised scope.

---

## Project Report

The detailed Week 02 practical report, including methodology, tools used, observations, scan results, and recommendations, is available below.

---

## Author

**Leisha Santoshkumar**  
Cybersecurity Intern – Networkwalks
**Internship:** Networkwalks  
**Program/Batch:** B084C-Networkwalks  
**Domain:** Cybersecurity  
**Week:** 02  
**Modules:** W2-PM1 and W2-PM5

---



