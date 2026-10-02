# 🔐 Week 4 — Penetration Testing & Vulnerability Assessment

## 📌 Overview

This repository contains my **Week 4 / Milestone 4 Penetration Testing & Vulnerability Assessment** project.

The assessment focused on identifying security weaknesses within an authorized web application environment, analyzing exposed resources, documenting security findings, assessing their impact, and providing remediation recommendations.

> **Disclaimer:** This assessment was performed within the authorized scope specified in the project documentation. Sensitive information discovered during testing is intentionally not published in this repository.

---

## 🎯 Objectives

The main objectives of the assessment were:

* Perform reconnaissance against the authorized target.
* Identify exposed directories and files.
* Analyze publicly accessible resources.
* Identify sensitive information exposure.
* Document vulnerabilities and their potential impact.
* Assign risk/severity levels.
* Provide practical remediation recommendations.
* Produce a professional penetration-testing report.

---

## 🧪 Assessment Details

| Category          | Details                                                               |
| ----------------- | --------------------------------------------------------------------- |
| Assessment Type   | Black-box Web Application Penetration Test & Vulnerability Assessment |
| Target            | Authorized web application                                            |
| Assessment Period | 5 days                                                                |
| Testing Scope     | Target domain and associated web infrastructure                       |
| Authorization     | Written authorization stated as granted                               |
| Testing Status    | Completed for the documented assessment objectives                    |

The assessment methodology covered reconnaissance and initial access, file analysis, data-exposure analysis, and security reporting.

---

## 🔍 Key Finding

### Publicly Accessible Database Backup

One of the primary findings was an accessible `/old/` directory that exposed a database backup file.

The directory could be enumerated without authentication, allowing the backup file to be identified and retrieved. This created a direct path from web-server misconfiguration to sensitive database disclosure.

### Sensitive Information Exposure

Analysis of the recovered database demonstrated exposure of categories of sensitive information including:

* Employee names
* Job titles
* Departments
* Email addresses
* Telephone numbers
* Salary information
* Shareholder information
* Shareholding details

These findings were documented as **High severity** in the assessment.

---

## 📊 Findings Summary

| ID      | Finding                                   | Severity         |
| ------- | ----------------------------------------- | ---------------- |
| F-01    | Publicly accessible database backup       | 🔴 High          |
| F-02    | Employee and salary information exposed   | 🔴 High          |
| F-03    | Shareholder information exposed           | 🔴 High          |
| F-04    | Directory listing exposes server contents | 🟠 Medium        |
| INFO-01 | `security.txt` unavailable                | ℹ️ Informational |

The report records the missing `security.txt` resource as informational because the collected evidence did not demonstrate a direct security impact from the missing file.

---

## 🛠️ Remediation Recommendations

The following remediation actions were identified during the assessment:

### 1. Remove Publicly Accessible Backups

Remove database backups and other sensitive files from publicly accessible web directories.

### 2. Disable Directory Listing

Disable directory indexing so that visitors cannot enumerate files within web-accessible directories.

### 3. Store Backups Outside the Web Root

Backups should be stored in protected backup infrastructure that cannot be directly accessed through HTTP/HTTPS.

### 4. Review Legacy Directories

Review directories such as:

```text
/old/
/backup/
/tmp/
```

and remove unnecessary `.sql`, `.zip`, `.tar`, `.gz`, `.bak`, `.old`, configuration, and environment files.

### 5. Rotate Exposed Credentials

Determine whether exposed backups contain credentials, API keys, password hashes, encryption keys, or other secrets and rotate them where necessary.

### 6. Improve Backup Security

Implement:

* Access controls
* Encryption at rest
* Retention policies
* Secure archival
* Secure deletion procedures

### 7. Implement Security Monitoring

Monitor web roots and sensitive paths for unexpected files, directory indexes, unusual downloads, and unauthorized access attempts.

---

## 📁 Repository Structure

week-4-penetration-testing-assessment/
│
├── README.md
│
├── report/
│   └── M4-Penetration-Testing-Report.pdf
│
├── evidence/
│   ├── directory-listing.png
│   └── sanitized-evidence.png
│
├── findings/
│   └── findings.md
│
└── remediation/
    └── remediation.md

Evidence uploaded to this repository should be sanitized to ensure that confidential information, credentials, personal data, and other sensitive content are not exposed.

📚 What I Learned

This assessment helped strengthen my understanding of:

Web application reconnaissance
Directory and file enumeration
Information disclosure vulnerabilities
Database backup exposure
Vulnerability classification
Risk assessment
Evidence-based reporting
Security remediation
Secure backup management

A key takeaway from this assessment is that legacy files and publicly accessible backups can significantly increase an application's attack surface.

⚠️ Ethical & Security Notice

This project was conducted as an authorized security assessment within the documented scope.

The repository does not intentionally contain:

Real credentials
Passwords or hashes
API keys
Confidential patient information
Personal employee information
Private shareholder records
Other sensitive production data

All screenshots and evidence shared publicly should be sanitized before publication.

📄 Assessment Report

The detailed penetration-testing report contains the complete findings, evidence, risk assessment, milestone status, and remediation recommendations.

Milestone 4 Status: ✅ Completed

The assessment concluded that the publicly exposed database backup represented a significant confidentiality risk requiring remediation.

🏷️ Tags

CyberSecurity PenetrationTesting WebSecurity VulnerabilityAssessment EthicalHacking InformationDisclosure OSINT InfoSec SecurityTesting CyberSecurityJourney
