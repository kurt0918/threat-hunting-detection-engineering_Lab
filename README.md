# threat-hunting-detection-engineering_Lab
Threat Hunting AND Detection Engineering Lab (Sentinel, Splunk, EDR, CTI).

This repository is my ongoing lab and portfolio as I deepen Threat Hunting, Detection Engineering, and Cyber Threat Intelligence integration across SIEM and EDR platforms.

It is designed to:
- Showcase real-world hunts, detections, and playbooks
- Demonstrate how I translate CTI (actors, TTPs, campaigns) into actionable detections
- Provide reusable templates and methodologies for SOCs and MSSPs

---

## 🧠 Focus Areas

- **Threat Hunting**
  - Microsoft Sentinel / KQL
  - Splunk / SPL
  - Microsoft Defender / EDR telemetry
  - SentinelOne (EDR) hunts
- **Detection Engineering**
  - Analytics rules in Sentinel
  - Correlation searches in Splunk
  - ATT&CK-mapped detection content
- **CTI → Detections**
  - Mapping threat reports & TTPs into hunts
  - Building actor-focused detection packages
- **Playbooks & Automation**
  - Hunt and incident playbooks
  - Python utilities for IOC enrichment, data extraction, and reporting

---

## 📁 Repository Structure

- `hunts/` – Concrete threat hunts with:
  - Hunt notebook, queries, findings, and MITRE mappings
- `detections/` – Production-oriented detection logic:
  - Sentinel analytics, Splunk correlation searches, Sigma rules
- `playbooks/` – Step-by-step response & hunting procedures
- `automation/` – Python/PowerShell utilities for CTI and log analysis
- `ctienrichment/` – Actor profiles, TTP mappings, and CTI → detection workflows
- `templates/` – Reusable documentation templates:
  - Hunt notebook
  - Detection spec
  - RCA template

---

## 🔍 Featured Projects (Work in Progress)

1. **Suspicious PowerShell Hunt (Microsoft Sentinel)**
   - Focus: Living-off-the-land (LOLBins) and suspicious PowerShell usage
   - Data Sources: Microsoft Sentinel (SecurityEvent, DeviceProcessEvents)
   - Output:
     - Hunt notebook (`hunts/sentinel/suspicious-powershell/hunt-notes.md`)
     - KQL query (`hunts/sentinel/suspicious-powershell/query.kql`)
     - Proposed detection rule (`detections/sentinel/analytic-rules/`)

2. **Ransomware Kill Chain Detection (Splunk + EDR)**
   - Focus: Pre-encryption behaviors (lateral movement, shadow copy deletion, suspicious backups)
   - Data Sources: Windows logs, EDR telemetry
   - Output:
     - SPL correlation searches
     - MITRE ATT&CK mapping
     - Response playbook

3. **CTI-Driven Supply Chain Intrusion Hunt**
   - Focus: Translating a public campaign (e.g., tampered installers or malicious updates) into hunts
   - Output:
     - TTP → log source mapping
     - Hunt queries in Sentinel/Splunk
     - Detection spec and actor profile

Additional projects will be added over time, with a bias toward:
- Realistic enterprise scenarios
- Repeatable methods for SOCs and MSSPs
- Practical value for interviews and consulting clients

---

## 🧾 Methodology (How I Hunt)

Every hunt in this repo follows a consistent structure:

1. **Trigger**
   - CTI report, anomalous telemetry, or hypothesis-based hunt
2. **Hypothesis**
   - Clear statement of what I expect to find and why
3. **Scope & Data Sources**
   - Log sources, time ranges, relevant fields
4. **Queries & Iteration**
   - Initial broad queries → refinement → pivoting
5. **Findings**
   - Observed behaviors, suspected activity, false positives
6. **Outcome**
   - Detection opportunities, playbooks updated, gaps identified

See: `templates/hunt-notebook-template.md`.

---

## 🧩 Roadmap

Planned additions:

- [ ] More Sentinel hunting notebooks
- [ ] Splunk correlation search packs by ATT&CK tactic
- [ ] Sigma rules mapped to SIEM-specific content
- [ ] Python tools to automate IOC sweeps and enrichments
- [ ] End-to-end incident simulations with RCA documentation

---

## 📫 Contact

If you’d like to collaborate, discuss CTI/hunting/detections, or explore consulting:

- **Name:** Kurt (Cyber Threat Intelligence / Threat Hunter)
- **Focus:** Threat Hunting • Detection Engineering • Incident Response • CTI
