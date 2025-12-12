## Week 02 — Theoretical Knowledge & Practical Application

This document contains the theory, hands-on labs, templates, and sample artifacts for the Week 02 VAPT training tasks. It is split into two main parts: Theoretical Knowledge and Practical Application. Use the provided templates and examples for lab documentation, reporting, and escalation.

---

## Theoretical Knowledge

### 1. Vulnerability Scanning Techniques

What to Learn:
- Understand scan types (network vs application), authenticated vs unauthenticated scanning, false positives and validation, and vulnerability scoring (CVSS v4.0).

Core Concepts:
- Scan Types:
	- Network scans — e.g., Nmap port/service discovery and version detection (nmap -sV).
	- Application scans — e.g., Nikto for common web flaws, Burp Scanner for web app logic issues.
	- Authenticated vs unauthenticated — credentialed scans provide deeper coverage and fewer false positives.
- Vulnerability Scoring:
	- Use CVSS v4.0 for consistent risk ranking (example: CVSS 8.8 = High for a remote code execution vector).
	- Example: Apache Struts (CVE-2017-5638) historically mapped to Critical severity.
- False Positives:
	- Always validate automated findings with manual checks (e.g., verify open ports, confirm web payloads, test authenticated endpoints).

Key Objectives:
- Configure scans to minimize noise and false positives.
- Validate high-impact findings manually and annotate evidence for reports.

How to Learn:
- Read the OWASP Testing Guide (WSTG) for web scanning techniques.
- Review NIST SP 800-115 for accepted scanning methodologies.
- Study historical incidents (e.g., WannaCry) to practice CVSS mapping and impact analysis.

### 2. Penetration Testing Techniques

What to Learn:
- End-to-end pentesting phases, methodologies (PTES, OWASP WSTG), exploitation basics, post-exploitation, and ethical considerations.

Core Concepts:
- Phases: Reconnaissance (OSINT with Shodan/Maltego), Scanning (Nessus/OpenVAS), Exploitation (Metasploit/sqlmap), Post-exploitation (privilege escalation, persistence), Reporting.
- Methodologies: PTES for scoping and repeatable phases; OWASP WSTG for web specifics.
- Ethics: Always obtain written authorization, define scope, and protect client data.

Key Objectives:
- Execute structured, authoritative, and ethical penetration tests following PTES or equivalent.

How to Learn:
- Study PTES phase-by-phase documentation.
- Work through OWASP WSTG web testing chapters.
- Read SANS pentest case studies for real-world techniques and reporting style.

### 3. Exploit Development Basics

What to Learn:
- Understand common exploit classes, how to examine PoCs, and safe exploit testing techniques.

Core Concepts:
- Exploit Types: Buffer overflows, SQL injection, XSS, RCE.
- Exploit Writing: Use Python or C to craft simple buffer overflow PoCs; examine Exploit-DB for sample PoCs.
- Mitigations: Learn ASLR, DEP/NX, stack canaries, WAFs, and patch management.

Key Objectives:
- Develop and test small, controlled exploits in isolated lab environments only.

How to Learn:
- Browse Exploit-DB for PoCs and study how exploits are constructed.
- Follow TCM Security exploit write-ups for practical guidance.
- Complete TryHackMe rooms for buffer overflows and exploit practice.

---

## Practical Application (Labs & Templates)

### 1. Vulnerability Scanning Lab

Activities & Tools:
- Tools: Nmap, OpenVAS (or Nessus), Nikto.
- Tasks: Run scans, triage results, prioritize vulnerabilities, document evidence and remediation.

Suggested Scan Steps:
1. Discovery with Nmap: nmap -sS -p- -T4 192.168.0.106
2. Service/version detection: nmap -sV -p 1-65535 192.168.0.106
3. Web directory and common issues: nikto -h http://192.168.0.106
4. Run OpenVAS/OpenVAS (or Nessus) authenticated and unauthenticated scans where possible.

Scan Results Template (Slack-friendly table):

| Scan ID | Vulnerability       | CVSS Score | Priority | Host           |
|--------:|--------------------:|-----------:|:--------:|:---------------|
| 001     | SQL Injection       | 9.1        | Critical | 192.168.0.106  |
| 002     | Open Port 445       | 6.5        | Medium   | 192.168.0.106  |

Test Case:
- Scan a Metasploitable2 VM with:

```bash
nmap -sV 192.168.0.106
```

- Run OpenVAS (or Nessus) and compare results. Prioritize using CVSS in a spreadsheet for sorting.

Prioritization:
- Use CVSS scores in Google Sheets to compute priority buckets (Critical: >=9, High: 7-8.9, Medium: 4-6.9, Low: <4). Include exploitability and asset value in final priority.

Reporting (Draft outline for Google Docs):
- Title: Critical Web Vulnerabilities
- Findings: e.g., [CVE-2021-41773] on Host: 192.168.0.106 — unauthenticated path traversal leading to information disclosure.
- Remediation: Patch Apache to fixed version, disable unused modules, restrict file permissions, and re-run scans.

Escalation (100-word email to developers with PoC):

Subject: Immediate action required — critical web vulnerability on 192.168.0.106

Hello team,

During routine testing, we discovered a critical web vulnerability (CVE-2021-41773) on 192.168.0.106 allowing path traversal and potential file disclosure. Proof-of-concept shows unauthenticated access to sensitive files. Recommend immediate patching to the vendor-supplied Apache update, restricting file permissions, and disabling unused modules. Please prioritize a hotfix and schedule a coordinated re-scan; I can provide the PoC and assist with verification. Confirm receipt and planned mitigation timeline.

Regards,
VAPT Analyst

(≈100 words)

### 2. Reconnaissance Practice

Activities & Tools:
- Tools: Maltego, Shodan, Sublist3r, Wappalyzer, WHOIS services, Google dorking.
- Tasks: Perform OSINT, enumerate assets, map services, capture evidence.

Recon Template (Google Docs friendly):
- Domain Info
- WHOIS
- Subdomains (Sublist3r)
- Exposed Services (Shodan)
- Technology Stack (Wappalyzer)

Asset Mapping (Slack-friendly log):

| Timestamp           | Tool    | Finding                                 |
|--------------------:|:--------|:----------------------------------------|
| 2025-08-18 10:00:00 | Shodan  | Exposed SSH on 192.168.0.106            |
| 2025-08-18 10:30:00 | Maltego | Subdomain: dev.example.com               |

Checklist:
- Check WHOIS and registrar
- Enumerate subdomains (Sublist3r / assetfinder)
- Identify tech stack (Wappalyzer)
- Check SSL/TLS configuration and headers

Recon 50-word summary (example):

Found multiple public-facing assets via Shodan and Maltego. dev.example.com hosts a web server exposing outdated server headers and SSH reachable from a permissive ACL. Collected WHOIS, subdomains, and service fingerprints; next steps: targeted vulnerability scans and prioritized follow-up on externally accessible SSH and web endpoints.

### 3. Exploitation Lab

Activities & Tools:
- Tools: Metasploit, Burp Suite, sqlmap, manual PoC verification, Exploit-DB.
- Tasks: Simulate exploitation in lab, capture evidence, record success/failure and payloads.

Exploit Simulation Log Template:

| Exploit ID | Description       | Target IP      | Status  | Payload      |
|-----------:|:------------------|:---------------|:-------:|:-------------|
| 003        | Tomcat RCE        | 192.168.0.106  | Success | Java Shell   |

Example Metasploit step (lab only):

1. Use exploit/multi/http/tomcat_mgr_login against Metasploitable2.
2. Capture successful session output and confirm limited, non-destructive payload.

Validation:
- Cross-check PoC with Exploit-DB and cite the PoC ID. Summarize results.

50-word exploit summary (example):

Used Metasploit to exploit Tomcat manager credentials on 192.168.0.106, achieving a Java shell. Confirmed access limited to non-destructive commands and documented session IDs. Verified PoC against Exploit-DB and recorded exact steps for reproducibility and remediation guidance.

### 4. Post-Exploitation Practice

Activities & Tools:
- Tools: Meterpreter, local privilege escalation modules, Volatility for memory analysis, sha256sum for evidence hashing.
- Tasks: Identify escalation paths, collect forensic evidence, document hashes and chain-of-custody.

Escalation Example:
- Use Metasploit exploit/windows/local/bypassuac in a lab context to practice safe escalation techniques. Record all commands and timestamps.

Evidence Collection Template:

| Item        | Description      | Collected By | Date       | Hash Value                              |
|:-----------|:----------------|:------------:|:----------:|:----------------------------------------|
| Config File | target.conf     | VAPT Analyst | 2025-08-18 | <SHA256_PLACEHOLDER>                     |

(Compute SHA256 locally with sha256sum or PowerShell: Get-FileHash -Algorithm SHA256 .\\target.conf)

### 5. Capstone Project: Full VAPT Cycle

Activities & Tools:
- Tools: Kali Linux, Metasploit, OpenVAS, Burp Suite, Google Docs for reporting.
- Tasks: Plan and execute an end-to-end pentest simulation in a lab environment (scope, recon, scan, exploit, post-exploit, report).

Simulation Example:
- Exploit DVWA with sqlmap for SQL injection: follow TryHackMe walkthroughs and capture SQLi payloads, evidence, and remediation steps.

Detection & Logging Template (OpenVAS findings):

| Timestamp           | Target IP      | Vulnerability | PTES Phase     |
|:-------------------:|:---------------|:--------------:|:---------------|
| 2025-08-18 12:00:00 | 192.168.0.106  | XSS           | Exploitation   |

Remediation Guidance:
- Suggest input validation, parameterized queries, prepared statements, output encoding, and re-scanning after fixes.

Reporting Requirements (deliverables):
- Technical PTES-formatted report (≈200 words summary required below)
- Non-technical 100-word executive briefing

200-word PTES report (example):

This engagement simulated a structured penetration test against a contained lab environment following PTES phases: scoping, reconnaissance, scanning, exploitation, and post-exploitation. Reconnaissance revealed several public assets and multiple subdomains. Scanning identified a high-severity SQL injection and multiple cross-site scripting (XSS) instances affecting the web application on 192.168.0.106. Exploitation of the SQL injection via sqlmap allowed retrieval of user table records in the lab, demonstrating data exposure risk. Post-exploitation confirmed no persistence mechanisms were deployed and privilege escalation attempts were contained within the lab VM. Recommendations prioritize immediate remediation of the SQL injection via parameterized queries and input validation, patching web frameworks, improving logging/monitoring for suspicious queries, and performing a credential rotation for affected accounts. Re-scan after remediation and perform a focused validation test. The test was conducted in a lab environment with no production data; all activity was authorized. Evidence, timestamps, and exact PoC commands are included in the attached technical appendix.

100-word non-technical briefing (example):

We performed an authorized security test on a lab instance to identify weaknesses that could be exploited by attackers. The test found a critical web vulnerability that could allow attackers to access sensitive data and other issues that increase the overall risk. We recommend urgent code fixes (input validation and prepared statements), patching, and a scheduled re-test once remediation is complete. These steps will significantly reduce the chance of successful attacks and protect sensitive information. We can assist with remediation validation and follow-up testing.

---

## Notes & Next Steps

- Use the included templates to record your lab runs.
- Keep all testing within authorized environments.
- For each lab, produce a short Google Doc with findings and evidence, and a Slack-friendly summary table for quick sharing.

## Files to produce after each lab
- Technical Google Doc report (detailed findings, PoCs, logs)
- Google Sheet with CVSS prioritization
- Slack-friendly tables and a short executive briefing (100 words)

---

End of Week 02 material.

