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

👉 Detailed report: **Week-01/README.md**

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

👉 Detailed report: **Week-02/README.md**

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

# 🧰 **Tools Used Across All Weeks**

### **Network & Port Scanning**

* Nmap

### **Vulnerability Scanning**

* OpenVAS
* Nikto

### **Web Application Testing**

* Burp Suite Community
* OWASP ZAP

### **Exploitation Frameworks**

* Metasploit
* SQLMap

### **Analysis & Monitoring**

* Wireshark

### **Documentation**

* Dradis CE
* CherryTree

---

# 📘 **Theoretical Knowledge Across All Weeks**

* NIST Cybersecurity Framework
* VAPT Methodology (Recon → Scan → Enumeration → Exploitation → Reporting)
* OWASP Top 10
* Risk Assessment & CVSS Scoring
* Compliance frameworks (GDPR, HIPAA, ISO 27001, CIS Benchmarks)
* Secure configuration principles
* Patch & vulnerability management lifecycle
* Defense-in-depth security model

---

# 🧩 **Key Takeaways**

1. Open-source tools are powerful and production-ready
2. Automated scanning ≠ manual exploitation
3. Compliance improves baseline but not full security
4. Proper documentation is critical
5. Continuous monitoring is essential
6. Authentication & encryption remain common failure points
7. Misconfigurations are the #1 root cause of vulnerabilities

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

