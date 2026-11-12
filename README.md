# PENETRATION TESTING REPORT
## FOOTPRINTING & NETWORK SCANNING PHASES

**W2-PM-FINAL | CYBERSECURITY & ETHICAL HACKING | NETWORKWALKS**

| Project Details | Information |
|---|---|
| **Intern Name** | Raj Ghimire |
| **Program / Batch** | NetworkWalks – B084 |
| **Date** | 12 November 2026 |
| **Modules Completed** | W2-PM1 (Multiple Kali Tools), W2-PM5 (Zenmap Scanning) |
| **Client / Target** | NetworkWalks (authorized reconnaissance), Own Local Network |
| **Permission Secured** | Yes |
| **Phases Covered** | Phase 1: Reconnaissance & Footprinting; Phase 2: Scanning & Network Discovery; Phase 3-5: In Progress  |
---

## 1. Liability Disclaimer

All activities documented in this repository were performed within the authorized scope of the assigned internship exercises or on systems and networks owned by me. The materials are intended for educational and research purposes only. Unauthorized access or testing of systems without appropriate permission is prohibited. The author is not responsible for any misuse of the tools or information presented in this repository.

## 2. Introduction

This report documents the practical activities completed during Week 02 of my Cybersecurity & Ethical Hacking internship at NetworkWalks.

The project covers two modules: footprinting and reconnaissance of the `networkwalks.com` domain using six Kali Linux tools (W2-PM1), and network discovery on my own local network using Zenmap (W2-PM5).

The activities focused on gathering publicly available information, identifying website technologies, examining DNS infrastructure, and discovering active hosts within a local network.

## 3. Tools Used

| Tool | Purpose |
|---|---|
| Kali Linux | Environment used for reconnaissance |
| whois | Retrieve domain registration information |
| whatweb | Identify website technologies and components |
| nslookup | Resolve domain names to IP addresses |
| curl -I | Examine HTTP response headers |
| wafw00f | Identify Web Application Firewall technology |
| dnsrecon | Enumerate DNS records |
| Zenmap (Nmap GUI) | Discover active hosts and network devices |
| Windows CMD | Identify local network configuration |

## 4. Activities Performed

### 4.1 Footprinting & Reconnaissance

Reconnaissance was performed against `networkwalks.com` using six Kali Linux tools. Each tool helped collect a different category of information about the target domain.

| Tool | Command | Key Observation |
|---|---|---|
| whois| `whois networkwalks.com` | Identified GoDaddy as the registrar and retrieved domain registration and name server information. |
| whatweb | `whatweb networkwalks.com` | Identified Apache, WordPress 7.1.4 and WP Download Manager 3.3.76. |
| nslookup | `nslookup networkwalks.com` | Resolved the domain to `192.232.216.135`. |
| curl -I | `curl -I https://networkwalks.com` | Returned HTTP 200 OK and exposed HTTP headers and the WordPress REST API endpoint. |
| wafw00f | `wafw00f networkwalks.com` | Identified ModSecurity (SpiderLabs) as the Web Application Firewall. |
| dnsrecon | `dnsrecon -d networkwalks.com` | Identified DNS, mail, TXT, SPF and service-related records. |

These activities provided an overview of the domain's registration details, web technologies, server information and DNS infrastructure.

### 4.2 Network Scanning with Zenmap

For the second activity, I used Zenmap to perform host discovery on my own local network.

I first identified the local network configuration and subnet using Windows Command Prompt. I then used Zenmap's Ping Scan profile to discover active devices.

**Target Network:**

```bash
192.168.0.0/24
```

**Nmap Command:**

```bash
nmap -sn 192.168.0.0/24
```

**Scan Results:**

The scan identified three active hosts within the local subnet.

| IP Address | Status | MAC Address |
|---|---|---|
| 192.168.0.1 | Up | F4:F2:6D:AF:95:38 |
| 192.168.0.100 | Up | Not displayed |
| 192.168.0.101 | Up | 3E:77:FD:26:A5:01 |

The scan covered 256 IP addresses and completed in approximately 4.91 seconds.

I also reviewed the network topology in Zenmap and saved the resulting topology report in PDF format.

## 5. Risk Analysis / Impact

Based on the information gathered during reconnaissance and network scanning, the following potential security considerations were identified.

| # | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
|---|---|---|---|---|
| 1 | Web technology information exposed | WhatWeb identified WordPress and plugin versions. | May assist technology fingerprinting and further security research. | Medium |
| 2 | Server IP identifiable | Nslookup resolved the domain to `192.232.216.135`. | Reveals the network location of the web service. | Low |
| 3 | HTTP technical information exposed | cURL returned server headers and the `/wp-json/` endpoint. | May assist further information gathering. | Low |
| 4 | WAF technology identifiable | Wafw00f identified ModSecurity. | Reveals information about the website's security infrastructure. | Low |
| 5 | DNS infrastructure information exposed | DNSRecon identified DNS, mail and service records. | Helps build a broader infrastructure profile. | Medium |
| 6 | Unidentified local network device | Zenmap discovered host `192.168.0.101`. | Unknown devices should be verified and accounted for. | Low |

**Note:** These findings represent observations from information gathering and network discovery. They are not confirmed vulnerabilities. No exploitation or vulnerability validation was performed during these exercises.

## 6. Recommendations

Based on the observations, the following security practices are recommended:

1. **Review exposed technology information:** Regularly review publicly visible web technologies, CMS platforms and plugin versions.
2. **Keep software updated:** Maintain current versions of website platforms, plugins and server components.
3. **Review HTTP headers:** Avoid unnecessary disclosure of technical information and review security-related headers.
4. **Monitor DNS records:** Periodically review DNS configurations and remove unnecessary records.
5. **Maintain WAF protection:** Keep Web Application Firewall configurations and security rules updated.
6. **Perform regular network discovery:** Periodically scan internal networks to identify active devices.
7. **Investigate unknown devices:** Verify unfamiliar devices connected to the network.
8. **Maintain network documentation:** Keep device inventories and network topology information updated.
9. **Follow authorized testing practices:** Perform reconnaissance and scanning only within an approved scope.

## 7. Conclusion

During Week 02 of my Cybersecurity & Ethical Hacking internship at NetworkWalks, I completed practical activities covering footprinting, reconnaissance and network scanning.

I used six Kali Linux tools to gather domain and website information and Zenmap to identify active devices on my local network.

These exercises helped me understand how information gathering and network discovery contribute to the initial stages of a security assessment. I also gained practical experience in analyzing tool outputs, identifying potential security considerations and documenting technical findings.

Overall, this project strengthened my understanding of reconnaissance methodologies and the importance of conducting security assessments responsibly and within an authorized scope.

## 8. Evidences Collected

All screenshots, command outputs and supporting documents are available in the `evidence/` directory.

### 8.1 Footprinting & Reconnaissance

| Tool | Evidence |
|---|---|
| whois | `evidence/whois.png` |
| whatweb | `evidence/whatweb.png` |
| nslookup | `evidence/nslookup.png` |
| curl -I | `evidence/curl-headers.png` |
| dnsrecon | `evidence/dnsrecon.png` |
| wafw00f | `evidence/wafw00f.png` |

### 8.2 Network Scanning

| Activity | Evidence |
|---|---|
| Zenmap Host Discovery | `evidence/zenmap-scan.png` |
| Network Topology | `evidence/local-network-topology.pdf` |

---

## 👤 Author

**Raj Ghimire**  
Cybersecurity & Ethical Hacking Intern  
NetworkWalks | Batch B084

## 📌 Project Information

- **Program:** Cybersecurity & Ethical Hacking Internship
- **Organization:** NetworkWalks
- **Project:** Week 02 – Footprinting & Network Scanning
- **Modules:** W2-PM1 and W2-PM5
- **Repository:** GitHub

---

*End of Report*
