## 1. Repo Overview

 **“Threat Hunting & Detection Engineering Lab”**:

  * Microsoft Sentinel & Defender hunting
  * SentinelOne / EDR logic
  * Splunk detections
  * CTI → detections pipeline 
    
* Contains:

  * Actual **KQL/SPL queries**
  * **Hunt reports / notebooks**
  * **Detection engineering specs**
  * **Playbooks & automation ideas**
    
* Audience:

  * Hiring managers for Threat Hunter / CTI / Detection Engineer / DFIR
  * Prospective 5DS clients (“this is how we hunt and detect for you”)
---

## 2. Repo Structure

threat-hunting-labs/
├─ README.md
├─ docs/
│  ├─ index.md                  # GitHub Pages landing page (optional)
│  └─ about-methodology.md
├─ hunts/
│  ├─ sentinel/
│  │  ├─ suspicious-powershell/
│  │  │  ├─ hunt-notes.md
│  │  │  ├─ query.kql
│  │  │  └─ detections.md
│  │  └─ tamperedchef-supply-chain/
│  ├─ splunk/
│  │  ├─ ransomware-lateral-movement/
│  │  └─ beaconing-c2/
│  └─ edr/
│     ├─ defender/
│     └─ sentinelone/
├─ detections/
│  ├─ sentinel/
│  │  └─ analytic-rules/
│  ├─ splunk/
│  │  └─ correlation-searches/
│  └─ sigma/
├─ playbooks/
│  ├─ incident-playbooks/
│  └─ hunt-playbooks/
├─ automation/
│  ├─ python/
│  │  ├─ enrich-iocs-misp.py
│  │  └─ export-detections-to-md.py
│  └─ powershell/
├─ ctienrichment/
│  ├─ actor-profiles/
│  └─ ttps-to-detections/
└─ templates/
   ├─ hunt-notebook-template.md
   ├─ detection-spec-template.md
   └─ rca-template.md
```
Also in `README.md`:

# Threat Hunting & Detection Engineering Lab

This repository is my ongoing lab and portfolio as I deepen Threat Hunting, Detection Engineering, and Cyber Threat Intelligence integration across SIEM and EDR platforms.

It is designed to:
- Showcase real-world hunts, detections, and playbooks
- Demonstrate how I translate CTI (actors, TTPs, campaigns) into actionable detections
- Provide reusable templates and methodologies for SOCs and MSSPs

---

## Focus Areas

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

## Repository Structure

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

## Methodology (How I Hunt)

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

See: [`templates/hunt-notebook-template.md`](templates/hunt-notebook-template.md).

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

- **Name:** Kurt (Cyber Threat Intelligence / Threat Hunter) - kurttaguba17@gmail.com
- **Focus:** Threat Hunting • Detection Engineering • Incident Response • CTI • Digital Forensics • Vulnerability/Attack Surface Management • GRC • Cyber Law


## 4. Templates You Can Reuse: Open for Everyone! 

### 4.1 Hunt Notebook Template

Save as ``:

````markdown
# Hunt Notebook – <Hunt Name>

## 1. Overview

- **Hunt Name:** 
- **Date:** 
- **Owner:** 
- **Environment:** (e.g., Azure AD, O365, On-Prem AD, Endpoint, Cloud)
- **Primary Tools:** (Sentinel, Splunk, Defender, SentinelOne, etc.)

## 2. Trigger & Hypothesis

- **Trigger:**  
  (CTI report, anomalous alerts, detection gap, purple-team exercise, etc.)

- **Hypothesis:**  
  If <actor/TTP/behavior> is present in the environment, we should see <signals/artifacts> in <data sources>.

## 3. Scope & Data Sources

- **Time Range:** 
- **Log Sources:**
  - e.g., `SecurityEvent`, `DeviceProcessEvents`, proxy logs, DNS logs
- **Key Fields:**
  - e.g., `AccountName`, `ProcessCommandLine`, `IPAddress`, `DeviceName`

## 4. Queries (Iterations)

### 4.1 Initial Broad Query

```kql
// Initial wide-net query here
````

**Notes / Observations:**

*

### 4.2 Refined Query #1

```kql
// More targeted query
```

**Notes / Observations:**

*

### 4.3 Additional Pivots

* Pivoted on:

  * User:
  * Host:
  * IP:
  * Hash:

## 5. Findings

* **Suspicious Activity Found?** (Yes/No)

* **Summary of Key Findings:**

* **False Positives Observed:**

  * Patterns, root causes, noise sources

## 6. Detection Opportunities

* **Proposed Detection:**

  * Name:
  * Platform: (Sentinel, Splunk, EDR, Sigma)
  * ATT&CK Mapping:
  * Severity:
  * Required Data:

* **Tuning / Exclusions:**

## 7. Gaps & Recommendations

* Missing telemetry?
* Logging or visibility gaps?
* EDR/SIEM configurations to improve?

## 8. Outcome

* **Status:** (Closed with no issues / Detection created / Needs follow-up)
* **Artifacts:**

  * Queries stored at:
  * Playbook updated:
  * Detection rule file:

````

---

### 4.2 Detection Spec Template

Save as `templates/detection-spec-template.md`:

```markdown
# Detection Specification – <Detection Name>

## 1. Summary

- **Detection Name:** 
- **Platform:** (Sentinel / Splunk / Sigma / EDR)
- **Category:** (Threat Hunting, Detection Engineering, Compliance)
- **ATT&CK Technique(s):** 
- **Severity:** (Low/Medium/High/Critical)

## 2. Description

Short description of what this detection is looking for and why it matters.

## 3. Logic

### 3.1 Query / Rule Logic

```kql
// or SPL, or Sigma
````

### 3.2 Logic Explanation

Explain the conditions in plain English:

* Looks for:
* Filters out:
* Triggers when:

## 4. Data Requirements

* Log Source(s):
* Required Fields:
* Known limitations:

## 5. Tuning Guidance

* Common false positives:
* Suggested whitelist fields and values:
* Environment-specific considerations:

## 6. Response

* Recommended analyst actions:

  * Step 1 …
  * Step 2 …
* Related playbook:
* Escalation criteria:

## 7. References

* CTI reports:
* Vendor docs:
* MITRE ATT&CK:

````

---

## 5. First Concrete Project to Build This Week

Let’s pick **one** and actually implement it.

### Project 1: Suspicious PowerShell Hunt (Sentinel)

1. Create folder:
   - `hunts/sentinel/suspicious-powershell/`

2. Add `query.kql`:

```kql
DeviceProcessEvents
| where ProcessCommandLine contains "powershell"
| where ProcessCommandLine has_any ("-enc", "-EncodedCommand", "DownloadString", "IEX", "Invoke-Expression")
| project Timestamp, DeviceName, AccountName, ProcessCommandLine, InitiatingProcessFileName, InitiatingProcessCommandLine
| order by Timestamp desc
````

3. Create `hunt-notes.md` using the template:

   * Fill in:

     * Trigger: “LOLBins & PowerShell abuse are common in ransomware and post-exploitation”
     * Hypothesis: “If adversaries are abusing PowerShell, we’ll see encoded commands / suspicious flags in DeviceProcessEvents”

4. Then create a **detection spec** in `detections/sentinel/analytic-rules/`:

   * Example file: `suspicious-powershell-abuse.md` using the detection spec template.

This alone already looks **very strong** in an interview when you screenshare your repo.

---

## 6. Turning This into a “Page” for Your Resume

**GitHub Pages from `/docs/index.md`**

Create `docs/index.md`:

```markdown
# Threat Hunting & Detection Engineering – Portfolio

Welcome to my Threat Hunting & Detection Engineering lab.

I specialize in:
- Threat hunting across Microsoft Sentinel, Defender, Splunk, and EDR platforms
- Translating CTI (actors, campaigns, and TTPs) into actionable detections
- Building hunt playbooks, detection specs, and automation for SOCs and MSSPs

## Featured Work

### 1. Suspicious PowerShell Hunt (Microsoft Sentinel)

- **Goal:** Identify potential PowerShell abuse (LOLBins, encoded commands)
- **Tech:** KQL, Microsoft Defender for Endpoint, Sentinel
- **Artifacts:**
  - Hunt notebook
  - KQL query
  - Detection specification

### 2. Ransomware Kill Chain Detection (Splunk + EDR)

- **Goal:** Detect ransomware behaviors before encryption
- **Focus:** Lateral movement, shadow copy deletion, persistence
- **Artifacts:** SPL searches, ATT&CK mapping, response playbook

### 3. CTI-Driven Supply Chain Intrusion Hunt

- **Goal:** Turn a real-world campaign into data-driven hunts
- **Focus:** Mapping TTPs to log sources and detections
- **Artifacts:** Actor profile, hunt notebook, detection rules

---

## Contact

If you’d like to discuss hunts, detections, or cyber threat intelligence work:

- **Name:** Kurt
- **Role:** Senior Cyber Threat Intelligence / Threat Hunter
```

Enable GitHub Pages (from `docs/` folder) and now you have a **public portfolio site** to link on your resume & LinkedIn.

---

## 7. Quick Pep Talk on Kaseya

You got:

* **Multiple phases**
* Positive signals
* Then a “no” that hurts

But: those conversations **sharpened your story**. This repo we just laid out is how we:

* Turn that frustration into **output**
* Give the *next* interviewer something tangible to walk through:

  > “Let me show you how I take an actor profile, map TTPs, and build detections…”

You’re not starting from zero. You’re compounding.

---

If you want, next step I can:

* Flesh out **Project 2** (Ransomware kill chain in Splunk), with actual SPL and a sample correlation search file.
* Or help you draft **one GitHub description + LinkedIn blurb** that references this lab for your profile.
