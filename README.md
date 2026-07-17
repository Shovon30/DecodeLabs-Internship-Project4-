# 🛡️ System Vulnerability Checklist
### DecodeLabs Cybersecurity Internship | Batch 2026 | Project 4 (Optional Mastery Phase)

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=flat&logo=python&logoColor=white)
![Track](https://img.shields.io/badge/Track-Cybersecurity-red?style=flat)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat)
![Internship](https://img.shields.io/badge/DecodeLabs-Batch%202026-orange?style=flat)
![Optional](https://img.shields.io/badge/Milestone-Optional%20Mastery-purple?style=flat)

---

## 📌 Overview

This is **Project 4** of the DecodeLabs Cybersecurity Industrial Training Kit — an optional mastery-phase project. The goal is to build a **system vulnerability audit engine** in Python that scores a machine's security posture across three domains — password hygiene, software patch status, and user practices — and outputs a risk-ranked report with concrete remediation steps.

> *"A system's integrity is dynamic. The security auditor is the essential gatekeeper for organizational resilience."*
> — DecodeLabs, Batch 2026 Kit

Unlike Projects 1–3, this one is deliberately built to be run against a **real, personal machine** — not just sample data — as the training kit's own "Gatekeeper Rule" requires.

---

## 🎯 Project Goals

| Requirement | Status |
|---|---|
| Check weak passwords | ✅ |
| Check software update status | ✅ |
| Identify unsafe user practices | ✅ |
| Bonus: Weighted risk scoring (CVSS-style funnel) | ✅ |
| Bonus: Standalone printable checklist reference | ✅ |
| Bonus: 3-section professional Vulnerability Report generator | ✅ |

---

## 🧠 Core Concepts Applied

### The Shift to Proactive Defense

| Legacy View (Reactive) | Blue Team Mindset (Proactive) |
|---|---|
| Security as a product | Security as a continuous process |
| Defending single components | Proactive hunting |
| Reactive remediation | Assumes constant software decay |
| Assuming the perimeter is secure | Mitigating zero-days before exploitation |

### The Blueprint to Fortification — IPO Model

```
INPUT                    PROCESS                      OUTPUT
──────────────────      ──────────────────────       ─────────────────────
Establish the      →    Methodical Inspection    →   Threat Reporting
Baseline                Cross-reference against       Risk-ranked
(hardware, software,    the Vulnerability             vulnerability list +
network ports)          Checklist                     remediation roadmap
```

### This Project Reuses Your Own Prior Work

| Category | Reuses Logic From |
|---|---|
| Weak password detection | **Project 1** — Password Strength Checker's gate rule (`<8 chars = critical`) |
| Unsafe user practices | **Project 3** — Phishing Triage Engine's human-behavior red flags |
| Weighted risk scoring | **Project 3** — Same Low/Medium/High/Critical scoring pattern, applied to systems instead of messages |

A real security engineer doesn't reinvent logic per task — this project is built the same way.

---

## ⚙️ The Three Audit Categories

### Step 1 — The Identity Front Door
| Check | Standard (NIST 800-63B) |
|---|---|
| Password length | 12+ characters — length over forced complexity |
| MFA | Phishing-resistant (FIDO2/WebAuthn/passkeys) over SMS/voice codes |
| Password reuse | Unique per account |
| Default/vendor passwords | Must be changed immediately on setup |

### Step 2 — Software Decay & Patch Management
> **The Auditor's Rule:** Delaying an update is explicitly accepting a risk.

- OS support status (End-of-Life = critical finding)
- Days since last update (>90 days = high risk)
- Automatic update status
- Antivirus/EDR presence and definition freshness
- Known unpatched critical CVEs
- Shadow IT detection (unapproved applications)

### Step 3 — Auditing the Human Perimeter
- Password sharing between colleagues
- Passwords written on paper or stored in plaintext
- Phishing susceptibility (clicking unsolicited links)
- Screen-lock discipline
- Personal/unapproved USB device usage
- Public Wi-Fi usage without a VPN
- Unauthorized software installation

---

## 📊 Risk Scoring — The CVSS-Style Funnel

Every finding carries a severity weight (1–4). Weights sum into a total score, which maps to a four-tier decision system:

| Score | Tier | Recommended Action |
|---|---|---|
| 0–3 | 🟢 LOW RISK | Maintain — monitor and revisit next cycle |
| 4–8 | 🟡 MEDIUM RISK | Schedule remediation within 30 days |
| 9–14 | 🟠 HIGH RISK | Remediate within 7 days |
| 15+ | 🔴 CRITICAL RISK | Remediate immediately — do not delay |

---

## 💻 Sample Output

```
══════════════════════════════════════════════════════════════
  DecodeLabs | System Vulnerability Report
  System: Remote Contractor Device
══════════════════════════════════════════════════════════════
  Findings (4):

  🔴 [Password & Identity] Password Too Short
      Evidence    : Length = 7
      Why it matters: Under 8 characters is an immediate brute-force
      risk (same gate rule as Project 1's Password Strength Checker).
      Remediation : Enforce a minimum 12-character passphrase.

  🟠 [Software & Patch Mgmt] OS Update Overdue
      Evidence    : 100 days since last update
      Why it matters: The Auditor's Rule: delaying an update is
      explicitly accepting a risk.
      Remediation : Apply all pending OS updates now.

  🟡 [Software & Patch Mgmt] Auto Update Disabled
  🟡 [User Practices] Unencrypted Public Wifi
------------------------------------------------------------------
  Category Risk Breakdown:
    Password & Identity       : 4
    Software & Patch Mgmt     : 5
    User Practices            : 2
------------------------------------------------------------------
  Total Risk Score : 11
  Classification   : 🟠  HIGH RISK
  Recommended Action: Remediate within 7 days
══════════════════════════════════════════════════════════════
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.9 or higher (uses `from __future__ import annotations` for broader compatibility)
- No external libraries required — standard library only

### Installation

```bash
git clone https://github.com/Shovon30/DecodeLabs-Internship-Project4-.git
cd DecodeLabs-Internship-Project4-
```

### Run

```bash
python3 system_vulnerability_checklist.py
```

### Modes

| Mode | Description |
|---|---|
| `[1]` Run Sample Audits | 4 systems spanning Low → Critical risk |
| `[2]` Audit My Own System | Interactive real self-assessment (the actual deliverable) |
| `[3]` View Checklist | Printable reference card, in-terminal |
| `[4]` Generate Report | Builds the 3-section professional Vulnerability Report from the last audit |

---

## 🧪 Sample Dataset — Full Risk Spectrum

| Profile | Score | Tier |
|---|---|---|
| Hardened Workstation | 0 | 🟢 LOW RISK |
| Typical Employee Laptop | 7 | 🟡 MEDIUM RISK |
| Remote Contractor Device | 11 | 🟠 HIGH RISK |
| Neglected Legacy Server | 54 | 🔴 CRITICAL RISK |

---

## 📄 Anatomy of the Vulnerability Report

The training kit requires a professional 1-page report with exactly three sections — `generate_report_template()` builds this automatically from any completed audit:

1. **Flaws Found (The Diagnosis)** — every finding with its CVSS-style severity weight
2. **Remediation Actions (The Treatment)** — the exact fix for each flaw
3. **Hardened Verification (The Proof)** — terminal commands to run *after* remediation, confirming the fix took effect (`Get-BitLockerVolume`, `fdesetup status`, etc.)

---

## 📁 Project Structure

```
DecodeLabs-Internship-Project4/
│
├── system_vulnerability_checklist.py   # Main audit engine
├── HARDENING_CHECKLIST.md              # Standalone reference card (2nd deliverable)
└── README.md                           # Project documentation
```

---

## 🔒 Design Notes

- **Weighted, category-scored aggregation** — mirrors the CVSS methodology (Base/Threat/Environmental) rather than a flat pass/fail check.
- **Acronym-safe label formatting** — a small `prettify_label()` helper prevents `.title()` from mangling security acronyms (`MFA`, `OS`, `CVE`, `USB`) into broken casing.
- **Sample profiles tuned to span all four risk tiers** — deliberately rebalanced so Low, Medium, High, and Critical are each represented distinctly, rather than clustering at the extremes.
- **Built to run against a real machine** — Mode 2 is the actual deliverable the training kit asks for, not just a demo.

---

## 🔗 Project Chain

| Project | Focus | Status |
|---|---|---|
| Project 1 — Password Strength Checker | Validation & Entropy | ✅ Completed |
| Project 2 — Basic Encryption & Decryption | Cryptography & Confidentiality | ✅ Completed |
| Project 3 — Phishing Awareness Analysis | Threat Detection & Human Firewall | ✅ Completed |
| Project 4 — System Vulnerability Checklist | Proactive Hardening & Risk Assessment | ✅ Completed (Optional Mastery) |

This project is the capstone of the track: it takes the password logic from Project 1, the human-risk scoring from Project 3, and extends both into a full system-level audit — proving the skills compose, not just repeat.

---

## 👤 Author

**Shovon** — Cybersecurity Track Intern
DecodeLabs Industrial Training Kit | Batch 2026

---

## 📜 License

Built as part of the DecodeLabs Internship Program for educational and portfolio purposes.
