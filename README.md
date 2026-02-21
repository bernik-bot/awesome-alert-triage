# 🚨 Awesome Alert Triage [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of **free and open-source** tools, platforms, and resources for security analysts doing day-to-day alert triage — from first alert to closed ticket.

Built for SOC analysts, blue teamers, and incident responders who need to move fast without spending money. Every tool here is free, open-source, or has a meaningful free tier.

**Pull requests welcome.** If you use it daily and it's free, add it.

---

## Contents

- [🧭 The Triage Workflow](#-the-triage-workflow)
- [🔍 IP & Domain Enrichment](#-ip--domain-enrichment)
- [🗂️ File & Hash Analysis](#️-file--hash-analysis)
- [🌐 URL & Web Analysis](#-url--web-analysis)
- [📧 Email & Phishing Analysis](#-email--phishing-analysis)
- [🧪 Sandboxes & Dynamic Analysis](#-sandboxes--dynamic-analysis)
- [🧠 Threat Intelligence Platforms](#-threat-intelligence-platforms)
- [📡 IOC Feeds & Blocklists](#-ioc-feeds--blocklists)
- [🔎 OSINT & Pivoting](#-osint--pivoting)
- [🛠️ SOAR & Orchestration (Open Source)](#️-soar--orchestration-open-source)
- [📋 Case Management & IR Tracking](#-case-management--ir-tracking)
- [🔐 SIEM & Log Analysis](#-siem--log-analysis)
- [🧰 Endpoint Triage & Forensics](#-endpoint-triage--forensics)
- [🔑 Credential & Data Breach Lookup](#-credential--data-breach-lookup)
- [📚 Playbooks & SOPs](#-playbooks--sops)
- [🧑‍💻 Training & Labs](#-training--labs)
- [📖 References & Frameworks](#-references--frameworks)

---

## 🧭 The Triage Workflow

Alert triage follows a repeatable loop. Every tool in this list maps to one or more stages:

```
ALERT RECEIVED
      │
      ▼
1. ENRICH      → Gather context on IPs, domains, hashes, URLs
      │
      ▼
2. CORRELATE   → Cross-reference IOCs against threat intel
      │
      ▼
3. INVESTIGATE → Sandbox, analyze artifacts, pivot on indicators
      │
      ▼
4. DECIDE      → True positive / False positive / Escalate
      │
      ▼
5. RESPOND     → Contain, document, close or escalate
```

> **Analyst tip:** The goal of triage is not to investigate everything fully — it's to make a fast, confident decision. Enrichment tools help you get there without wasting time on false positives.

---

## 🔍 IP & Domain Enrichment

The first thing you do with any alert involving a network indicator.

- [AbuseIPDB](https://www.abuseipdb.com/) - Community-powered IP reputation database. Check if an IP has been reported for abuse, with category and confidence score. Free API available.
- [VirusTotal](https://www.virustotal.com/) - Analyze IPs, domains, hashes, and URLs against 70+ engines. The analyst's Swiss Army knife. Free tier available.
- [Shodan](https://www.shodan.io/) - Search engine for internet-connected devices. Great for understanding what's running on a suspicious IP. Free tier available.
- [Censys](https://search.censys.io/) - Internet-wide scan data for IPs and domains. Free tier available for individuals.
- [GreyNoise](https://www.greynoise.io/) - Tells you if an IP is scanning the internet (noise) vs. targeting you specifically. Free community tier.
- [IPinfo](https://ipinfo.io/) - Fast IP geolocation, ASN, and org lookup. Free API for low volume.
- [MXToolbox](https://mxtoolbox.com/) - DNS, blacklist, and email infrastructure lookups. Completely free.
- [DNSlytics](https://dnslytics.com/) - Reverse DNS, IP history, and domain analytics. Free.
- [RiskIQ Community](https://community.riskiq.com/) - PassiveTotal replacement. Passive DNS, WHOIS, and certificate history. Free community tier.
- [Robtex](https://www.robtex.com/) - IP and domain investigation tool with graph relationships. Free.
- [BGP Ranking](https://bgpranking.circl.lu/) - Ranks ASNs based on malicious activity. Free, run by CIRCL (CERT Luxembourg).
- [ThreatMiner](https://www.threatminer.org/) - Data mining for threat intelligence with IP, domain, and hash search. Free.
- [Hurricane Electric BGP](https://bgp.he.net/) - ASN lookup and BGP routing information. Free.

---

## 🗂️ File & Hash Analysis

When you have a suspicious file or a hash from an EDR alert.

- [VirusTotal](https://www.virustotal.com/) - Multi-engine file and hash analysis. Search existing reports without uploading. Free.
- [FileScanner.online](https://filescanner.online/) - Fast, free online file scanner. Upload files and scan against multiple detection engines without sending samples to external vendors. Great for quick triage.
- [MalwareBazaar](https://bazaar.abuse.ch/) - Malware sample repository from abuse.ch. Search by hash, tag, or signature. Free and community-driven.
- [Loki](https://github.com/Neo23x0/Loki) - Free host-based IOC scanner using YARA rules and hash databases. Runs locally, no data leaves your environment.
- [YARA](https://github.com/VirusTotal/yara) - Pattern matching tool for malware identification. The foundation of most file triage workflows.
- [ClamAV](https://www.clamav.net/) - Open source antivirus engine. Scan files locally without sending data out. Great for air-gapped environments.
- [Detect-It-Easy (DiE)](https://github.com/horsicq/Detect-It-Easy) - Determine file type, packer, compiler, and linker. Essential for initial static triage of executables.
- [ExifTool](https://exiftool.org/) - Read, write, and edit file metadata. Reveals author info, creation timestamps, and embedded paths that can be pivots.
- [hashdeep](https://github.com/jessek/hashdeep) - Compute and audit file hashes (MD5, SHA1, SHA256, Tiger, Whirlpool). Useful for integrity verification.
- [PEframe](https://github.com/guelfoweb/peframe) - Open source static analysis for PE (Windows executable) files and malicious Office documents.
- [nsrllookup](https://github.com/rjhansen/nsrllookup) - Query NIST's National Software Reference Library to check if a file hash is known-good software.
- [Assemblyline](https://github.com/CybercentreCanada/assemblyline) - Open source, scalable file triage and malware analysis system from the Canadian Centre for Cyber Security.

---

## 🌐 URL & Web Analysis

For phishing links, suspicious redirects, and drive-by download investigations.

- [URLScan.io](https://urlscan.io/) - Scans URLs and renders the page in a sandbox, capturing screenshots, DOM, network requests, and IOCs. Free and heavily used.
- [URLScanner.online](https://urlscanner.online/) - Free, fast URL scanner with malicious URL detection. Submit suspicious links directly for instant verdict without exposing your endpoint.
- [URLhaus](https://urlhaus.abuse.ch/) - abuse.ch project tracking malicious URLs used for malware distribution. Search and lookup. Free.
- [Google Safe Browsing](https://transparencyreport.google.com/safe-browsing/search) - Check if Google has flagged a URL as malicious. Free, no account needed.
- [PhishTank](https://phishtank.org/) - Community-verified phishing URL database. Free lookup and API.
- [CheckPhish](https://checkphish.ai/) - Real-time phishing URL detection using AI. Free for low volume.
- [dnstwist](https://github.com/elceef/dnstwist) - Domain permutation engine for detecting typosquatting, phishing, and brand abuse. Run locally, free and open source.
- [Unfurl](https://github.com/obsidianforensics/unfurl) - Deconstructs and visualizes URLs to expose encoded data, timestamps, and tracking parameters. Open source.
- [VirusTotal](https://www.virustotal.com/) - URL analysis against 70+ URL scanners. Free.
- [IsItPhishing](https://isitphishing.org/) - Real-time phishing detection. Free API for analysts.
- [Sucuri SiteCheck](https://sitecheck.sucuri.net/) - Free website malware and blocklist scanner.

---

## 📧 Email & Phishing Analysis

The #1 alert type in most SOCs. Analyze headers, links, and attachments without clicking anything.

- [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx) - Parse raw email headers to trace routing, check SPF/DKIM/DMARC, and identify spoofing. Free.
- [Google Admin Toolbox - Message Header](https://toolbox.googleapps.com/apps/messageheader/) - Google's email header analyzer. Simple and fast. Free.
- [PhishTool](https://www.phishtool.com/) - Purpose-built phishing email analysis platform. Free community tier. Extracts IOCs from emails automatically.
- [mailheader.org](https://mailheader.org/) - Simple email header parser. Free.
- [EmailRep](https://emailrep.io/) - Reputation lookup for email addresses. Check if an address has been associated with malicious activity. Free API.
- [Have I Been Pwned](https://haveibeenpwned.com/) - Check if an email address appears in known data breaches. Free.
- [Hunter.io](https://hunter.io/) - Verify if an email address format is legitimate for a domain. Free tier.
- [URLScan.io](https://urlscan.io/) - Submit phishing links from emails for safe analysis. Free.
- [URLScanner.online](https://urlscanner.online/) - Quickly verify suspicious links extracted from phishing emails. Free.
- [Phishtank](https://phishtank.org/) - Cross-reference extracted URLs against known phishing database. Free.
- [VirusTotal](https://www.virustotal.com/) - Scan email attachments by hash or upload. Free.

> **Analyst tip:** Never click links in suspected phishing emails. Extract the URL, defang it (`hxxps://`), and use URLScan.io or URLScanner.online instead.

---

## 🧪 Sandboxes & Dynamic Analysis

When static analysis isn't enough and you need to see what a file or URL actually *does*.

- [Any.run](https://app.any.run/) - Interactive online sandbox. Watch malware execute in real time and see network connections, file drops, registry changes. Free community tier.
- [Hybrid Analysis](https://www.hybrid-analysis.com/) - Powered by CrowdStrike Falcon Sandbox. Free for community use. Excellent automated reports.
- [Tria.ge](https://tria.ge/) - Fast, multi-OS sandbox (Windows, Linux, macOS, Android). Free community tier with public reports.
- [Joe Sandbox Community](https://www.joesandbox.com/) - Deep behavioral analysis. Free community tier.
- [Cuckoo Sandbox](https://github.com/cuckoosandbox/cuckoo) - The original open source, self-hosted malware sandbox. Full control, no data leaves your environment.
- [CAPE Sandbox](https://github.com/kevoreilly/CAPEv2) - Cuckoo fork with added focus on malware config extraction. Actively maintained. Open source.
- [Intezer Analyze](https://analyze.intezer.com/) - Genetic malware analysis — classifies files based on code reuse from known malware families. Free community tier.
- [Browserling](https://www.browserling.com/) - Test suspicious URLs in a live browser sandbox. Free tier available.
- [FileScanner.online](https://filescanner.online/) - Quick online file analysis without needing to stand up your own sandbox. Free.

---

## 🧠 Threat Intelligence Platforms

Aggregate, correlate, and share threat intelligence across your team and community.

- [MISP](https://www.misp-project.org/) - The gold standard open source threat intelligence platform. Share and correlate IOCs across organizations. Fully free and open source.
- [OpenCTI](https://github.com/OpenCTI-Platform/opencti) - Open source threat intelligence platform built around STIX2. Beautiful UI, free and open source.
- [Pulsedive](https://pulsedive.com/) - Free community threat intelligence platform. Enriches IOCs from open-source feeds with risk scoring. Free tier.
- [AlienVault OTX (Open Threat Exchange)](https://otx.alienvault.com/) - Massive community threat intelligence sharing platform. Free. Subscribe to "pulses" from researchers worldwide.
- [ThreatFox](https://threatfox.abuse.ch/) - abuse.ch platform for sharing IOCs related to malware C2 infrastructure. Free and community-driven.
- [YETI](https://github.com/yeti-platform/yeti) - Your Everyday Threat Intelligence — organizes observables, IOCs, TTPs, and threat knowledge in one place. Open source.
- [IntelOwl](https://github.com/intelowlproject/IntelOwl) - Open source threat intelligence aggregator that queries dozens of analyzers from a single API call. Self-hosted, free.
- [ThreatMiner](https://www.threatminer.org/) - Threat intelligence data mining portal. Free, no account needed for basic searches.
- [Cortex](https://github.com/TheHive-Project/Cortex) - Observable analysis and active response engine. Pairs with TheHive. Open source.

---

## 📡 IOC Feeds & Blocklists

Free, community-maintained IOC feeds to enrich your SIEM, firewall, or TIP.

- [abuse.ch Feeds](https://abuse.ch/) - Suite of free, community-driven threat feeds: URLhaus, MalwareBazaar, ThreatFox, Feodo Tracker, SSL Blacklist. Essential.
- [Emerging Threats (Proofpoint)](https://rules.emergingthreats.net/) - Free Snort/Suricata rulesets updated daily. Community rules are completely free.
- [MISP Warning Lists](https://github.com/MISP/misp-warninglists) - Lists of well-known indicators to prevent false positives (e.g., Google IPs, CDNs, known-good domains).
- [FireHOL IP Lists](https://iplists.firehol.org/) - Aggregates 350+ IP blocklists with analytics and overlap detection. Free.
- [Bambenek Consulting Feeds](https://osint.bambenekconsulting.com/feeds/) - OSINT feeds based on malicious DGA (Domain Generation Algorithm) analysis. Free for non-commercial use.
- [Unit 42 IOCs (Palo Alto)](https://github.com/pan-unit42/iocs) - Indicators from Unit 42 public threat reports. Free GitHub repo.
- [ESET Malware IOCs](https://github.com/eset/malware-ioc) - IOCs from ESET's public investigations. Free GitHub repo.
- [Cyber Cure Free Intel](https://www.cybercure.ai/free-cyber-threat-intelligence/) - Free daily updated IP, URL, and hash threat feeds.
- [OpenPhish](https://openphish.com/) - Free phishing URL feed, updated in real time.
- [PhishTank](https://phishtank.org/) - Community-verified phishing database with free API.

---

## 🔎 OSINT & Pivoting

When you need to go deeper on a suspicious actor, infrastructure, or campaign.

- [Maltego CE](https://www.maltego.com/ce/) - Visual link analysis for OSINT investigations. Community Edition is free.
- [SpiderFoot](https://github.com/smicallef/spiderfoot) - Automated OSINT collection and attack surface mapping. Open source, self-hosted.
- [theHarvester](https://github.com/laramies/theHarvester) - Gather emails, names, subdomains, IPs, and URLs from public sources. Open source.
- [Recon-ng](https://github.com/lanmaster53/recon-ng) - Full-featured web reconnaissance framework. Modular and open source.
- [Shodan](https://www.shodan.io/) - Pivot on IP infrastructure — find other hosts on the same ASN, certificate, or banner. Free tier.
- [Censys Search](https://search.censys.io/) - Internet-wide scan data. Pivot on TLS certificates, banners, and services. Free for individuals.
- [WHOIS / RDAP](https://lookup.icann.org/) - ICANN WHOIS lookup. Free and no account required.
- [SecurityTrails](https://securitytrails.com/) - Historical DNS, WHOIS, and subdomain data. Free tier includes 50 API queries/month.
- [IntelligenceX](https://intelx.io/) - Search Tor, I2P, data leaks, and public web. Free tier with limited results.
- [Grep.app](https://grep.app/) - Search across 500,000+ public GitHub repositories for IOCs, strings, or malware signatures. Free.

---

## 🛠️ SOAR & Orchestration (Open Source)

Automate the repetitive parts of triage so analysts can focus on decisions.

- [TheHive](https://github.com/TheHive-Project/TheHive) - Scalable, open source security incident response platform for SOCs and CSIRTs. Pairs with MISP and Cortex. Free.
- [Shuffle](https://github.com/Shuffle/Shuffle) - Open source SOAR platform with a visual workflow builder and hundreds of app integrations. Free community tier.
- [n8n](https://github.com/n8n-io/n8n) - Open source workflow automation. Not security-specific but widely used for security automation pipelines. Self-hosted is free.
- [Velociraptor](https://github.com/Velocidex/velociraptor) - Open source endpoint visibility and collection platform. Great for remote triage and threat hunting. Free.
- [IRIS](https://github.com/dfir-iris/iris-web) - Collaborative incident response platform. Analysts can share investigations at a technical level. Free and open source.
- [Cortex](https://github.com/TheHive-Project/Cortex) - Observable analysis engine. Feed it an IP, hash, or URL and it queries dozens of analyzers automatically. Free and open source.
- [GRR Rapid Response](https://github.com/google/grr) - Google's open source remote live forensics and incident response framework. Free.

---

## 📋 Case Management & IR Tracking

Track incidents from alert to closure without losing context.

- [TheHive](https://github.com/TheHive-Project/TheHive) - Full-featured, open source incident case management. Native integration with MISP and Cortex. Free.
- [DFIR IRIS](https://github.com/dfir-iris/iris-web) - Web-based collaborative IR platform. Create cases, tasks, timelines, and evidence. Free.
- [FIR (Fast Incident Response)](https://github.com/certsocietegenerale/FIR) - Lightweight, agile incident management platform from CERT Société Générale. Free and open source.
- [DFIRTrack](https://github.com/dfirtrack/dfirtrack) - Incident response tracking with cases, tasks, and system artifacts. Open source.
- [Timesketch](https://github.com/google/timesketch) - Google's open source tool for collaborative forensic timeline analysis. Free.

---

## 🔐 SIEM & Log Analysis

Ingest, search, and correlate your logs at scale.

- [Wazuh](https://github.com/wazuh/wazuh) - Free, open source SIEM and XDR. Threat detection, integrity monitoring, incident response, and compliance in one platform. Massive community.
- [Graylog Open](https://graylog.org/products/source-available/) - Log management and SIEM with fast search. Open source core is free.
- [OpenSearch Security](https://opensearch.org/) - AWS's fork of Elasticsearch. Full-text log search and security analytics dashboards. Free.
- [Elastic SIEM (Free Tier)](https://www.elastic.co/siem) - SIEM on top of the Elastic Stack. Free self-hosted deployment.
- [Sigma](https://github.com/SigmaHQ/sigma) - Generic, vendor-agnostic detection rule format. Convert Sigma rules to Splunk SPL, KQL, Elastic, and more. The Rosetta Stone of detection. Free.
- [HELK](https://github.com/Cyb3rWard0g/HELK) - Hunting ELK — pre-configured Elasticsearch, Logstash, Kibana stack with threat hunting analytics. Open source.

---

## 🧰 Endpoint Triage & Forensics

When you need to collect artifacts from a potentially compromised host.

- [Velociraptor](https://github.com/Velocidex/velociraptor) - Remote endpoint interrogation and artifact collection at scale. Open source and free. One of the best tools in modern IR.
- [KAPE](https://www.kroll.com/en/insights/publications/cyber/kroll-artifact-parser-extractor-kape) - Kroll Artifact Parser and Extractor. Fast, targeted artifact collection. Free.
- [Loki](https://github.com/Neo23x0/Loki) - Free IOC scanner. Run against endpoints during triage to detect known malware by hash, YARA rule, or filename.
- [FastIR Collector](https://github.com/SekoiaLab/Fastir_Collector) - Collects forensic artifacts from live Windows systems quickly. Free.
- [Volatility 3](https://github.com/volatilityfoundation/volatility3) - Industry-standard open source memory forensics framework. Analyze RAM dumps for injected code, hidden processes, and network connections.
- [DFIR-ORC](https://github.com/dfir-d3/dfir-orc) - Reliable collection of forensic artifacts from Windows systems. From ANSSI. Free.
- [Osquery](https://github.com/osquery/osquery) - SQL-powered endpoint visibility. Query your endpoints like a database. Free and open source.
- [Eric Zimmerman Tools](https://ericzimmerman.github.io/) - Suite of free Windows forensic tools (MFTECmd, PECmd, RECmd, etc.). Essential for Windows artifact parsing.
- [Autoruns](https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns) - Sysinternals tool to enumerate all persistence mechanisms on Windows. Free from Microsoft.
- [Process Monitor](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon) - Real-time Windows file system, registry, and process activity monitoring. Free from Microsoft.
- [Wireshark](https://www.wireshark.org/) - The network traffic analysis tool. Capture and analyze packets. Free and open source.

---

## 🔑 Credential & Data Breach Lookup

Check if credentials from an alert or incident have been exposed.

- [Have I Been Pwned](https://haveibeenpwned.com/) - Check email addresses against 13+ billion breached records. Free. API for bulk queries.
- [DeHashed](https://dehashed.com/) - Search breached databases for emails, usernames, IPs, hashes. Paid, but has limited free lookups.
- [Leak-Lookup](https://leak-lookup.com/) - Free tier for searching breach databases.
- [IntelligenceX](https://intelx.io/) - Search pastes and data leaks for emails, domains, and credentials. Free tier.

---

## 📚 Playbooks & SOPs

Don't start from scratch. Adapt these battle-tested incident response playbooks.

- [IRM by CERT Société Générale](https://github.com/certsocietegenerale/IRM) - Incident Response Methodologies for common attack types (ransomware, phishing, DDoS, web compromise). Free.
- [Incident Response Workflows (ENISA)](https://www.enisa.europa.eu/publications/good-practice-guide-for-incident-management) - ENISA good practice guide for incident management. Free.
- [PagerDuty IR Docs](https://response.pagerduty.com/) - PagerDuty's open source incident response documentation. Free.
- [NIST SP 800-61](https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final) - Computer Security Incident Handling Guide. The authoritative reference. Free PDF.
- [Awesome Incident Response](https://github.com/meirwah/awesome-incident-response) - Comprehensive list of IR tools and resources.
- [Ransomware Playbook (CISA)](https://www.cisa.gov/stopransomware/ransomware-guide) - CISA's step-by-step ransomware response guide. Free.
- [Sigma Rules Repository](https://github.com/SigmaHQ/sigma) - Community detection rules for dozens of attack patterns. Free.
- [MITRE ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/) - Map detections and coverage against the ATT&CK framework. Free, browser-based.

---

## 🧑‍💻 Training & Labs

Sharpen triage skills in real-world scenarios without a real incident.

- [TryHackMe](https://tryhackme.com/) - Hands-on security training with guided paths for SOC analysts. Free tier available.
- [CyberDefenders](https://cyberdefenders.org/) - Blue team CTF challenges simulating real incident scenarios. Free.
- [Blue Team Labs Online](https://blueteamlabs.online/) - Hands-on DFIR, security operations, and threat hunting challenges. Free tier.
- [Splunk BOTS](https://bots.splunk.com/) - Boss of the SOC — practice SPL queries and incident investigation on real datasets. Free.
- [DetectionLab](https://github.com/clong/DetectionLab) - Vagrant/Terraform lab environment with security tooling pre-configured. Build your own triage lab locally. Free.
- [HELK](https://github.com/Cyb3rWard0g/HELK) - Pre-built threat hunting ELK stack for practicing log analysis. Free.
- [LetsDefend](https://letsdefend.io/) - SOC analyst simulation with real alerts to triage. Free tier.
- [Malware Traffic Analysis](https://www.malware-traffic-analysis.net/) - Huge library of PCAP files with exercises for network-based malware analysis. Free.
- [SANS Cyber Aces](https://www.sans.org/cyberaces/) - Free foundational cybersecurity courses from SANS.

---

## 📖 References & Frameworks

The theory and frameworks behind effective triage.

- [MITRE ATT&CK](https://attack.mitre.org/) - The universal adversary tactics and techniques knowledge base. Use it to contextualize alerts and understand attacker behavior.
- [MITRE D3FEND](https://d3fend.mitre.org/) - Countermeasures knowledge graph. Maps defensive techniques to ATT&CK. Free.
- [Pyramid of Pain (David Bianco)](http://detect-respond.blogspot.com/2013/02/the-pyramid-of-pain.html) - Foundational model for understanding the value of different IOC types. Required reading.
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework) - Identify, Protect, Detect, Respond, Recover. Free.
- [PICERL Incident Response Lifecycle](https://www.sans.org/white-papers/33901/) - Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned.
- [11 Strategies for a World-Class SOC (MITRE)](https://www.mitre.org/news-insights/publication/11-strategies-world-class-cybersecurity-operations-center) - The most practical SOC management paper ever written. Free PDF.
- [Sigma Rule Writing Guide](https://github.com/SigmaHQ/sigma/wiki/Rule-Creation-Guide) - How to write and contribute detection rules. Free.
- [The DFIQ Project](https://dfiq.org/) - Digital Forensics Investigative Questions — structured approach to investigative questions and their answers. Free.

---

## Contributing

Contributions are very welcome! Please read the [contribution guidelines](CONTRIBUTING.md) before submitting a PR.

To add a tool:
1. Check it is **free or has a meaningful free tier**
2. It must be **actively maintained** (updated in the last 2 years)
3. It must be **directly useful for alert triage** (not just generally useful for security)
4. Add it in **alphabetical order** within its section
5. Keep the description to **one sentence** that explains the triage use case

---

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0)

To the extent possible under law, the authors have waived all copyright and related rights to this work.
