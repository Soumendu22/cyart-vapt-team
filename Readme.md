# 🛡️ **CyArt VAPT Team – Security Assessment Repository**

### *Comprehensive Vulnerability Assessment & Penetration Testing Program*

Welcome to the **CyArt VAPT Team GitHub Repository**, containing the complete documentation, reports, findings, tools, methodologies, and theory learned across **four weeks of hands-on VAPT training**.

The repository includes structured reports for each week, covering real-world security assessment workflows using **open-source tools**, industry frameworks, and professional reporting standards.

---

# 📂 **Repository Structure**

```
CYART-VAPT-TEAM/
│
├── Week_01/
│   ├── VAPT_Report_Week_01.pdf
│   └── Week_01.md
│
├── Week_02/
│   ├── Reports/
│   │   ├── Capstone_VAPT/
│   │   │   └── Capstone_VAPT.pdf
│   │   │
│   │   ├── Exploitation_and_Post_Exploitation/
│   │   │   └── Exploitation_&_Post_Exploitation.pdf
│   │   │
│   │   ├── Reconnaissance/
│   │   │   └── Reconnaissance.pdf
│   │   │
│   │   └── Vulnerability_Scanning/
│   │       ├── Email.md
│   │       └── Vulnerability_Scanning.pdf
│   │
│   ├── Screenshots/
│   │   └── (All screenshots used for evidence)
│   │
│   ├── Summary/
│   │   ├── Exploitation/
│   │   │   └── summary.md
│   │   │
│   │   ├── Non_Technical/
│   │   │   └── Non_technical_summary.md
│   │   │
│   │   ├── Reconnaissance/
│   │   │   └── Recon_summary.md
│   │   │
│   │   └── Technical/
│   │       └── Technical_summary.md
│   │
│   ├── VAPT_Report_Week_02.pdf
│   └── Week_02.md
│
├── Week_03/
│   ├── Reports/
│   │   ├── Advanced_Exploitation/
│   │   │   └── Email.md
│   │   │
│   │   ├── Capstone_VAPT/
│   │   │   ├── Non_Technical_Summary.md
│   │   │   └── PTES.md
│   │   │
│   │   ├── Post-Exploitation_and_Evidence_Collection/
│   │   │   └── Evidence_Summary.md
│   │   │
│   │   ├── Reporting_Practice/
│   │   │   └── Non_Technical_Summary.md
│   │   │
│   │   └── Web_Application_Testing/
│   │       └── Summary.md
│   │
│   ├── Screenshots/
│   │   └── (All screenshots used for evidence)
│   │
│   ├── Task_Outline.md
│   └── Week_03.md
│
├── Week_04/
│   ├── Reports/
│   │   ├── Advanced_Exploitation_Lab/
│   │   │
│   │   ├── API_Security_Testing/
│   │   │
│   │   ├── Capstone_VAPT/
│   │   │
│   │   ├── Mobile_Application_Testing/
│   │   │   └── Mobile_Application_Testing.md
│   │   │
│   │   ├── Network_Protocol/
│   │   │
│   │   └── Privilege_Escalation/
│   │
│   ├── Screenshots/
│   │   └── (All screenshots used for evidence)
│   │
│   ├── Summary/
│   │   ├── Non_Technical_Summary.md
│   │   │
│   │   ├── API_Testing/
│   │   │   └── API_Summary.md
│   │   │
│   │   ├── Mobile_Application_Testing/
│   │   │   └── Mobile_Application_Testing_Summary.md
│   │   │
│   │   ├── Network_Protocol/
│   │   │   └── Network_Protocol_Summary.md
│   │   │
│   │   └── Privilege_Escalation/
│   │       └── Privilege_Escalation_Summary.md
│   │
│   └── Week_04.md
│
└── Readme.md
```

---

# 🧭 **Purpose of This Repository**

This repository serves as a **complete documentation hub** for the CyArt VAPT Internship. It showcases:

* Real-world security assessment workflows
* Detailed VAPT reports with executive summaries
* Hands-on exploitation labs
* CVSS scoring & risk matrices
* Compliance analysis (GDPR, HIPAA, ISO 27001, OWASP Top 10)
* Tools & methodologies used
* Evidence, screenshots, commands, and PoCs
* Weekly theory notes & learning outcomes

It is ideal for:
✔️ Portfolio presentation
✔️ Internship evaluation
✔️ VAPT methodology learning
✔️ Security research references

---

# 📅 **Weekly Breakdown**

Below is an overview of what each week contains.

---

# 🔵 **Week 01 – Fundamentals of VAPT & Initial Assessment**

### **Topics Covered**

* Understanding security assessments
* NIST Cybersecurity Framework
* VAPT methodology
* Vulnerability scanning basics
* Documentation fundamentals

### **Key Activities**

* Environment study
* Nmap scanning
* OpenVAS baseline vulnerability scan
* Nikto web scanning
* Initial evidence collection

### **Major Findings**

* Default credentials
* Outdated software
* SQLi and XSS
* Weak encryption
* Authentication failures

👉 Detailed report: **Week-01/Week_01.md**

---

# 🟢 **Week 02 – Deep Vulnerability Analysis & Manual Testing**

### **Topics Covered**

* Manual validation of scanner findings
* Web application testing (OWASP Top 10)
* Burp Suite methodology
* CVSS scoring in depth
* Reporting standards (Dradis, CherryTree)

### **Key Activities**

* Testing SQL Injection with SQLMap
* XSS payload creation
* Authentication bypass analysis
* Misconfiguration deep dive
* CVE research & mapping

### **Common Findings**

* Stored/Reflected XSS
* Broken access control
* Weak session management
* Insecure design patterns

👉 Detailed report: **Week-02/Week_02.md**

---

# 🟣 **Week 03 – Advanced Exploitation & Professional Reporting**

### **Topics Covered**

* Advanced vulnerability exploitation techniques
* Exploit chains and customization
* Web application penetration testing (OWASP Top 10)
* Post-exploitation and evidence collection
* Professional reporting and stakeholder communication

### **Key Activities**

* Chaining exploits (XSS to RCE)
* Customizing PoCs from Exploit-DB
* DVWA testing with Burp Suite & sqlmap
* Privilege escalation techniques
* Evidence collection and chain-of-custody
* PTES report creation

### **Major Focus Areas**

* Exploit customization and obfuscation
* Manual web application testing
* Technical and non-technical reporting
* Stakeholder communication
* Full VAPT cycle simulation

👉 Detailed outline: **Week-03/Week_03.md**

---

# 🔴 **Week 04 – Advanced Exploitation & Comprehensive Security Testing**

### **Topics Covered**

* Advanced exploitation techniques (exploit chaining, custom PoCs)
* API security testing (OWASP API Top 10)
* Privilege escalation and persistence mechanisms
* Network protocol attacks (SMB relay, MitM)
* Mobile application penetration testing (OWASP Mobile Top 10)
* Comprehensive VAPT reporting and remediation strategies

### **Key Activities**

* Multi-stage exploit chains (XSS to RCE)
* Custom exploit development and defense evasion (ROP, ASLR bypass)
* API testing with Burp Suite and Postman
* Privilege escalation using LinPEAS/WinPEAS
* SMB relay attacks and ARP spoofing
* Mobile app analysis with MobSF and Frida
* Full VAPT engagement simulation

### **Major Focus Areas**

* Exploit chaining and customization
* API vulnerability exploitation (BOLA, GraphQL injection)
* Advanced privilege escalation (SUID, kernel exploits)
* Network protocol exploitation
* Mobile security assessment (static and dynamic analysis)
* Professional PTES reporting for technical and non-technical audiences

### **Tools Introduced**

* Ghidra (reverse engineering)
* Postman (API testing)
* LinPEAS/WinPEAS (privilege escalation)
* PowerSploit (Windows exploitation)
* Responder (NTLM credential harvesting)
* Ettercap (MitM attacks)
* MobSF (mobile security framework)
* Frida (dynamic instrumentation)
* Drozer (Android security)

👉 Detailed outline: **Week-04/Week_04.md**

---

# 🧰 **Tools Used Across All Weeks**

### **Network & Port Scanning**

* Nmap

### **Vulnerability Scanning**

* OpenVAS
* Nikto

### **Web Application Testing**

* Burp Suite Community
* OWASP ZAP
* Postman (API testing)

### **Exploitation Frameworks**

* Metasploit
* SQLMap
* Python (custom exploit development)

### **Analysis & Monitoring**

* Wireshark

### **Privilege Escalation**

* LinPEAS
* WinPEAS
* PowerSploit

### **Network Protocol Attacks**

* Responder
* Ettercap

### **Mobile Application Testing**

* MobSF (Mobile Security Framework)
* Frida
* Drozer

### **Reverse Engineering**

* Ghidra

### **Documentation**

* Dradis CE
* CherryTree
* Google Docs

---

# 📘 **Theoretical Knowledge Across All Weeks**

* NIST Cybersecurity Framework
* VAPT Methodology (Recon → Scan → Enumeration → Exploitation → Reporting)
* OWASP Top 10 (Web Applications)
* OWASP API Top 10
* OWASP Mobile Top 10
* Risk Assessment & CVSS Scoring
* Compliance frameworks (GDPR, HIPAA, ISO 27001, CIS Benchmarks)
* Secure configuration principles
* Patch & vulnerability management lifecycle
* Defense-in-depth security model
* Advanced exploitation techniques (exploit chaining, ROP, ASLR bypass)
* Network protocol attacks (SMB relay, MitM, ARP spoofing)
* Privilege escalation and persistence mechanisms
* Mobile application security (static and dynamic analysis)
* API security testing methodologies
* PTES (Penetration Testing Execution Standard)

---

# 🧩 **Key Takeaways**

1. Open-source tools are powerful and production-ready
2. Automated scanning ≠ manual exploitation
3. Compliance improves baseline but not full security
4. Proper documentation is critical
5. Continuous monitoring is essential
6. Authentication & encryption remain common failure points
7. Misconfigurations are the #1 root cause of vulnerabilities
8. Exploit chaining enables complex multi-stage attacks
9. API security is critical in modern application architectures
10. Mobile applications present unique security challenges
11. Network protocol vulnerabilities persist in legacy systems
12. Effective communication bridges technical and business stakeholders
13. Privilege escalation and persistence are key to maintaining access
14. Defense evasion techniques (ROP, polymorphic payloads) bypass modern protections
15. Professional reporting requires tailoring content to diverse audiences

---

# 📝 **Contributors**

This repository is maintained by the **CyArt VAPT Intern Team**, as part of a practical cybersecurity training program.

---

# 📄 **Reports & Evidence**

Each weekly folder contains:

* Full PDF report
* Markdown summary
* Screenshots & PoC evidence
* Tool outputs
* Commands & payloads used

---

# ⭐ **How to Use This Repository**

You may use this repository to:

* Learn practical VAPT workflows
* Study real assessment structures
* Build your own portfolio
* Prepare for cybersecurity interviews
* Reference open-source security tools

---

