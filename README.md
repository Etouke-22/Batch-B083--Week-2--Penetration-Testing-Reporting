# Batch-B083--Week-2--Penetration-Testing-Reporting

### Week 2 | Cybersecurity Internship | Networkwalks

![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat)
![Type](https://img.shields.io/badge/Type-Reconnaissance-blue?style=flat)
![Tools](https://img.shields.io/badge/Tools-Kali%20Linux-blue?style=flat)

---

## Report Metadata

| Field | Details |
|---|---|
| **Pentester Name** | Etouke Cedric |
| **Program/Batch** | B083-Networkwalks |
| **Date** | 16 September 2026 |
| **Client/Target** | 1. Networkwalks (Granted permission)<br>2. My own local LAN |
| **Permission Secured?** | ✅ Yes |
| **Report ID** | W2-PM- |

---

## Modules Completed
- `W2-PM 1` — Multiple Kali Tools
- `W2-PM 2` — Attack with GHDB
- `W2-PM 3` — 
- `W2-PM 4` — Attack with theHarverster
- `W2-PM 5` — Zenmap/Nmamp Enumeration
  


# ⚠⚠ Disclaimer ⚠⚠

All security testing activities documented in this repository were conducted only against systems, networks, and applications for which I had appropriate authorization or that I personally owned and controlled.

The information and techniques presented in this report are intended strictly for educational, training, and authorized cybersecurity assessment purposes. They should not be used to access, scan, attack, or interfere with systems without explicit permission from the owner.

I do not support or encourage unauthorized access, data theft, disruption of services, or any other illegal activity. The responsibility for how the information, commands, and techniques contained in this repository are used rests entirely with the individual using them.

Unauthorized security testing may violate applicable laws and regulations and can result in legal, financial, academic, or professional consequences. Always obtain proper authorization and define the scope of testing before conducting any security assessment.


# Introduction

The second week of the cybersecurity practical focused on the initial stages of a penetration test, particularly reconnaissance, footprinting, information gathering, and network discovery.

The objective of these exercises was to understand how security professionals collect information about a target before conducting deeper security assessments. Different tools were used because each provides a different perspective of the target environment. Domain information was examined through WHOIS and DNS utilities, web-server information was inspected with cURL, Wafw00f was used to identify web application firewall technology, and DNSRecon was used to examine available DNS records.

Additional reconnaissance exercises involved Google Hacking Database (GHDB) techniques and theHarvester. These demonstrated how publicly available information can reveal details about an organization's external presence. Finally, Zenmap was used within an authorized local network to identify active devices and obtain a basic view of the network.

All testing should be performed only against systems for which appropriate authorization has been obtained.

## 🎯Objectives

The main objectives of the practical were:

Understand the purpose of reconnaissance and footprinting in penetration testing.
Gather publicly available information about an authorized domain.
Examine DNS and web-server information.
Identify technologies that are externally visible.
Understand how search engines can expose publicly indexed information.
Collect information from multiple public sources using theHarvester.
Discover active devices on an authorized local network.
Assess the security relevance of the information collected.
Document findings and distinguish reconnaissance observations from confirmed vulnerabilities.

## Tools and Technologies

The practical made use of several security and network-analysis tools.

Tool	Purpose
Kali Linux	Environment used for security reconnaissance and assessment activities <br>
WHOIS	Obtaining public domain-registration information
Nslookup	Resolving domain names through DNS
cURL	Examining HTTP response information
Wafw00f	Detecting web application firewall technology
DNSRecon	Enumerating publicly available DNS records
GHDB	Searching for information indexed by search engines
theHarvester	Collecting publicly available hosts, IP addresses, emails and related information
Zenmap	Performing graphical Nmap-based network discovery
Windows Command Prompt	Obtaining local network configuration



## Phases Covered

1. Reconnaissance & Information Gathering
2. Footprinting & Enumeration
3. Network Scanning & Discovery
4. Analysis & Recommendations
5. Conclusion & Documentation 


###  Reconnaissance Tools

- WHOIS
- nslookup
- DNSRecon
- WhatWeb
- WAFW00F
- CURL

###  Information Gathering

- WHOIS reconnaissance
- DNS enumeration
- Subdomain enumeration
- Technology identification
- WAF detection


# PM1  Reconnaissance and Footprinting

## WHOIS Enumeration

WHOIS was used to obtain publicly available registration information associated with the authorized domain.

The command used was:


```bash
> whois networkwalks.com
```
The output provided information such as the registrar, registration dates, domain name servers, and DNSSEC status.

This information is useful during reconnaissance because it provides an initial picture of how a domain is registered and which external infrastructure is associated with it. Although registration information is not normally considered a vulnerability by itself, it can contribute to an attacker's understanding of the organization's external presence.

## DNS Resolution with Nslookup

Nslookup was used to determine the IP address associated with the target domain.


```bash
> nslookup networkwalks.com
```

The resulting DNS information showed the address associated with the domain and the DNS server responsible for resolving the request.

From a penetration-testing perspective, DNS resolution is an important early step because it identifies the network destination associated with an externally accessible service. This information can subsequently be used during authorized assessment activities.

## HTTP Header Examination

cURL was used to inspect the HTTP response returned by the target web server.


```bash
> curl -I https://networkwalks.com
```

The response provided information about the HTTP status and various response headers. Depending on the configuration of the server, these headers may reveal information about the underlying web-server software, content-management system, caching mechanisms, or other components.

This demonstrates why organizations should carefully consider which technical details are exposed through HTTP responses. Information disclosed by headers may assist legitimate security testing, but it can also help an attacker fingerprint the technology used by a website.

## Web Application Firewall Detection

Wafw00f was used to determine whether a Web Application Firewall (WAF) was protecting the target.


```bash
> wafw00f networkwalks.com
```

The tool identified the WAF technology observed during the test.

The presence of a WAF is an important defensive control because it can inspect and filter potentially malicious web requests. However, detecting a WAF does not demonstrate that an application is completely secure. Proper security testing would still be required to evaluate the effectiveness of the application's defenses.

## DNS Enumeration

DNSRecon was used to collect publicly available DNS information.


```bash
> dnsrecon -d networkwalks.com
```


The enumeration provided records associated with the domain, such as A, AAAA, MX, NS, SOA, and other available records.

DNS records can reveal information about an organization's infrastructure, including web servers, mail servers, name servers, and other services. Consequently, unnecessary or outdated DNS records should be reviewed periodically and removed when they are no longer required.

## Web Technology Fingerprinting

A web technology fingerprinting tool such as WhatWeb can also be used to identify technologies running on a website.


```bash
> whatweb networkwalks.com
```

Only results that were successfully obtained during the practical should be included in the final report. If the tool fails to produce reliable output, the failed attempt should be documented rather than presenting an assumed result.

# PM2 Google Hacking Database Reconnaissance

The Google Hacking Database was examined to understand how search engines can unintentionally expose publicly accessible resources.

Search operators, commonly referred to as Google dorks, can be used to narrow search results to particular URLs, file types, titles, directories, or other characteristics.

The purpose of this exercise was not to exploit the discovered systems. Instead, it demonstrated how information that has already been indexed publicly may provide useful intelligence during reconnaissance.

Security Significance

From a defensive perspective, organizations should periodically examine what information about their infrastructure is publicly indexed. Sensitive administrative interfaces, directory listings, documents, cameras, configuration files, or other resources should not be unintentionally exposed through public search engines.

A search-engine result should also not automatically be interpreted as evidence of a vulnerability. Additional verification would be required to determine the actual security impact.

# PM4 Information Gathering with theHarvester

TheHarvester was used to demonstrate passive information gathering from publicly available sources.

A typical command is:


```bash
> theHarvester -d networkwalks.com -l <limit> -b <source>
```


The tool can collect information such as:

IP addresses
Hostnames
Email addresses
URLs
Subdomains
Autonomous System Numbers (ASNs)

## Single-Source Search

The first search configuration used a specific public information source.

```bash
> theHarvester -d networkwalks.com -l <limit> -b <source>
```


The results demonstrated that the amount of information obtained can vary considerably depending on the data source being queried.

A lack of results from one source does not necessarily mean that the target has no publicly available information. It may simply indicate that the selected source did not return useful data.

## Multi-Source Reconnaissance

A broader search can be performed using multiple available sources:


```bash
> theHarvester -d networkwalks.com -l <limit> -b all
```


Using several sources can produce a substantially broader view of an organization's external footprint.

The results should be documented using the actual output generated during the practical. Important categories include the number of discovered IP addresses, hosts, email addresses, URLs, and ASNs.

It is also important to document any limitations encountered during the exercise. Some theHarvester sources may require API credentials, meaning that unavailable services can affect the quantity and completeness of the collected information.

# PM5 Network Discovery with Zenmap

Zenmap was used to examine an authorized local network and identify active devices.

Before scanning, the local network configuration was determined using the operating system's network commands. This provided information such as the local IP address, subnet mask, and default gateway.

The appropriate subnet was then selected for the authorized scan.

For example:

```bash
> nmap -T4 -F <authorized-subnet>
```


Zenmap presented the scan results through a graphical interface, making it easier to identify active hosts and visualize relationships between devices.

Network discovery is particularly useful from a defensive perspective. Administrators can compare discovered devices with an approved asset inventory. An unfamiliar device may indicate a configuration problem, an unmanaged system, or another security issue requiring investigation.

# Risk Assessment

The information collected during reconnaissance can be categorized according to its potential security significance.

Finding	Potential Significance	Suggested Risk
Public domain-registration information	Helps build an external profile	Low
Discoverable server IP address	Reveals network location	Low
Technical HTTP information	Assists technology fingerprinting	Low
Identifiable WAF technology	Reveals part of the defensive architecture	Low
Detailed DNS records	May expose infrastructure relationships	Medium
Large number of externally visible hosts	Expands the infrastructure requiring monitoring	Medium
Public email addresses	Could assist phishing or social engineering	Low
Multiple ASNs	Provides information about network infrastructure	Low
Unexpected internal hosts	May indicate unmanaged or unauthorized devices	Medium
Publicly indexed resources	May provide additional reconnaissance information	Medium

These ratings should be treated as preliminary observations rather than confirmed vulnerabilities. Reconnaissance primarily identifies information that could be useful during a later assessment. Additional authorized testing is required before determining whether a specific weakness can actually be exploited.

# Recommendations

Based on the reconnaissance and network-discovery exercises, the following defensive measures are recommended:

Regularly review publicly available information about organizational domains and infrastructure.
Minimize unnecessary technical information exposed through web-server responses.
Periodically audit DNS records and remove obsolete entries.
Maintain and monitor the organization's externally exposed assets.
Ensure that the web application firewall is correctly configured and regularly updated.
Review publicly accessible email addresses and strengthen defenses against phishing and impersonation.
Periodically assess the organization's public-facing attack surface.
Conduct internal network discovery at regular intervals.
Compare discovered network devices against an approved asset inventory.
Investigate unknown or unexpected devices on internal networks.
Keep network diagrams and asset documentation current.
Perform penetration-testing activities only when appropriate authorization has been obtained.

# Conclusion

The practical exercises provided experience with several important stages of penetration testing, particularly reconnaissance, footprinting, passive information gathering, and network discovery.

The exercises demonstrated that significant information can be obtained from publicly available sources without directly exploiting a target. DNS records, HTTP responses, registration information, search-engine indexes, public datasets, and network-discovery tools can each contribute different pieces of information about an organization's digital environment.

The activities also emphasized the importance of interpreting reconnaissance results correctly. The discovery of an IP address, hostname, DNS record, email address, or technology does not automatically constitute a vulnerability. Such information should instead be treated as intelligence that may require additional authorized investigation.

Overall, the practical strengthened my understanding of the reconnaissance phase of cybersecurity and highlighted the importance of accurate documentation, evidence-based analysis, responsible testing, and maintaining an appropriate authorization scope.

# Tool / Technology	Purpose

|---|---|
| Kali Linux | 	Security-focused operating system used as the primary penetration-testing environment.|
| WHOIS |	Used to obtain publicly available domain registration and ownership information.|
| Nslookup	| Used to query DNS records and resolve domain names to IP addresses. |
cURL	Used to inspect HTTP responses and identify information exposed by web servers.
Wafw00f	Used to detect and identify Web Application Firewall (WAF) technologies.
DNSRecon	Used to enumerate and analyze publicly available DNS records and infrastructure.
GHDB	Used to demonstrate search-engine reconnaissance and identify publicly indexed information.
theHarvester	Used to gather publicly available information such as email addresses, hostnames, IP addresses, and URLs.
Zenmap	Graphical interface for Nmap, used to discover hosts and examine an authorized network.
Nmap	Used for network discovery and scanning of authorized systems and networks.
Windows Command Prompt	Used to obtain local network configuration and connectivity information.






