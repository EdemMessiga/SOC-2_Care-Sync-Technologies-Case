# SOC 2 Type I Readiness Assessment CareSync Technologies Inc.

**Framework:** AICPA Trust Services Criteria (2017, updated 2022) + PHIPA Integration
**Industry:** Healthcare SaaS Electronic Health Record (EHR) Platform
**Entity (Fictional):** CareSync Technologies Inc. Canadian Health IT SaaS serving 47 hospitals and 312 clinics
**Assessment Type:** SOC 2 Type I Control Design Adequacy (Pre-CPA Firm Engagement)
**Auditor:** Edem Messiga, ISO 27001 Certified Lead Auditor Privacy and Compliance Office
**Assessment Period:** May 1 to 23, 2026 (15 business days)

---

## Why Healthcare SaaS?

Healthcare is the highest-stakes environment for privacy and security compliance in Canada. A cloud EHR platform processes millions of patient records the most sensitive category of personal information under the dual weight of the Personal Health Information Protection Act (PHIPA), provincial privacy laws, and enterprise client SLA requirements. A GRC analyst working in or aspiring to work in Canadian health IT must understand both the AICPA Trust Services Criteria and Canada's health privacy legislative framework.

This project simulates a SOC 2 Type I readiness assessment for a fictional Canadian health IT company that is being required by its largest client Ontario Health to achieve SOC 2 Type II by Q1 2027. The Type I assessment is the prerequisite. Every finding in this project has both a SOC 2 dimension (which Trust Services Criterion is at risk?) and a PHIPA dimension (which legislative obligation is implicated?).

---

## Engagement Context

CareSync Technologies Inc. operates as an **agent of covered entities** under PHIPA meaning that when a hospital uses CareSync's EHR platform, CareSync is legally bound by the same PHI protection obligations as the hospital itself. This creates a dual compliance obligation that shapes every finding in this report.

The assessment was triggered by Ontario Health's enterprise contract requiring SOC 2 Type II by Q1 2027. CareSync has never been through a SOC 2 examination before. The Privacy and Compliance Office commissioned this internal readiness assessment to identify and remediate gaps before engaging a licensed CPA firm for the formal Type I examination.

---

## System in Scope

- Multi-tenant cloud EHR platform (AWS Canada Central and ca-west-1 DR)
- Approximately 4.2 million patient records including PHI under PHIPA (Ontario) and PIPA (Alberta)
- 47 hospital clients and 312 clinic clients across Ontario, Alberta, and British Columbia
- All five Trust Services Criteria categories assessed

---

## Key Findings

| Exception | Control | TSC | Finding | Rating |
|---|---|---|---|---|
| EX-001 | CS-P2.1 | P | PHI shared with ClinicalAI Corp for AI training no BAA, no consent, non-compliant de-identification. **Potential PHIPA breach requiring IPC notification assessment.** | **Critical** |
| EX-002 | CS-CC9.2 | CC | ClinicalAI Corp added to production without BAA or vendor risk assessment | High |
| EX-003 | CS-CC3.2 | CC | No insider threat monitoring program; UEBA not procured; 2 open curiosity access complaints suggesting systemic RBAC gap | High |
| EX-004 | CS-CC6.6 | CC | 8 former clinical staff accounts not deprovisioned at 3 client institutions | High |
| EX-005 | CS-CC6.1 | CC | 3 institutional super user accounts with unrestricted PHI access and no PHIPA justification | High |
| EX-006 | CS-CC7.1 | CC | PHI bulk download alerts muted without documentation genuine exfiltration could be missed | High |
| EX-008 | CS-P3.1 | P | Consent audit trail missing no history of consent changes | High |
| EX-009 | CS-CC4.2 | CC | No deficiency tracking register; 2 Q4 2025 deficiencies unresolved for 6 months | High |

**Overall Design Adequacy:** 14 of 32 controls fully designed (44%)
**Critical Findings:** 1 | **High Findings:** 10 | **Medium Findings:** 1
**SOC 2 Type I Readiness Opinion:** Not ready Critical finding (EX-001) must be resolved before CPA firm engagement

---

## Deliverables

| File | Description |
|---|---|
| `CareSync_SOC2_TypeI_Workbook.xlsx` | 3-tab workbook: Engagement Overview (system description, TSC coverage, regulatory context, compliance summary with formulas), Controls Matrix (32 controls with TSC criterion, control activity, healthcare-specific context, design status, PHIPA regulatory reference), Exception Log (12 exceptions with PHIPA implications, immediate actions, and remediation evidence requirements) |
| `CareSync_SOC2_TypeI_Report.docx` | Formal readiness report: critical breach escalation notice, healthcare regulatory framework table, detailed findings with PHIPA analysis for each, PHIPA-specific observations (insider threat, AI and PHI, multi-jurisdiction complexity), SOC 2 Type I readiness opinion, and CPA firm engagement conditions |

---

## What Makes This Project Realistic

**The ClinicalAI Corp scenario** is based on a real-world pattern: engineering teams in health IT companies frequently treat AI vendor pilots as technical decisions rather than privacy decisions, bypassing Privacy Officer review. The Ontario IPC issued specific guidance on health data AI use in 2025 precisely because this is an active compliance risk. This finding demonstrates understanding of the intersection between AI governance and Canadian health privacy law.

**PHIPA is integrated throughout** not treated as a separate checklist. Every control gap in this project is analyzed through both a SOC 2 lens (which TSC criterion is at risk?) and a PHIPA lens (which legislative section is implicated? has the IPC issued relevant guidance?). This dual-framework analysis is how a GRC practitioner in Canadian health IT actually thinks.

**Client relationship complexity** findings EX-004 (deprovisioning) and EX-005 (super user accounts) reflect the reality that a SaaS company cannot fully control what its clients do with its platform. The remediation for these findings is contractual and workflow-based, not purely technical a nuance that reflects real GRC practice.

**The 'policy exists but can be bypassed' gap** the ClinicalAI Corp situation, the alert muting (EX-006), and the secondary use review bypass (EX-010) all share the same root cause: policy-only controls that have no system-level enforcement. This is one of the most common findings in real SOC 2 readiness assessments and one of the most valuable lessons for a junior GRC practitioner to internalize.

---

## PHIPA-SOC 2 Mapping

| SOC 2 TSC | PHIPA Obligation | CareSync Risk |
|---|---|---|
| CC6.1 (Access Controls) | PHIPA s.29 minimum necessary access | Super user accounts without justification |
| CC6.6 (Access Revocation) | PHIPA s.12 ongoing safeguard obligation | Client-managed deprovisioning gap |
| CC7.1 (Anomaly Detection) | PHIPA s.12(2) detect inappropriate access | Muted PHI bulk download alerts |
| CC9.2 (Vendor Risk) | PHIPA s.17 third-party agent obligations | Missing BAAs (ClinicalAI, MedTranscribe) |
| P2.1 (Purpose Limitation) | PHIPA s.29 use limited to identified purposes | AI training use without consent |
| P3.1 (Consent) | PHIPA s.18 consent requirements | Missing consent audit trail |
| P4.1 (Secondary Use) | PHIPA ss.29,44 research and secondary use | No enforcement gate for secondary use review |

---

## Regulatory Context

| Law / Framework | Key Obligation Relevant to This Engagement |
|---|---|
| PHIPA (Ontario) | Primary framework safeguards, breach notification, consent, disclosure limits, IPC oversight |
| PIPA (Alberta) | Applies to 3 Alberta clinic clients separate consent and retention requirements |
| PIPEDA | Applies to inter-provincial data flows; breach reporting under SOR/2018-64 |
| Ontario Health BAA | SOC 2 Type II by Q1 2027; 99.9% uptime; 2-hour breach notification; annual DR test |
| Ontario IPC | Investigative and enforcement authority; guidance on AI and PHI, consent, de-identification |
| Bill C-27 / CPPA | Proposed federal successor to PIPEDA stricter consent, right to disposal, AI transparency |

---

## Skills Demonstrated

- SOC 2 Type I methodology across all five Trust Services Criteria
- PHIPA legislative analysis integrated with SOC 2 control assessment
- Healthcare AI governance and PHI de-identification standards (Ontario IPC guidance)
- Insider threat risk assessment in a PHI context
- Multi-jurisdiction privacy compliance (PHIPA, PIPA Alberta, PIPA BC)
- Vendor BAA review and third-party PHI risk assessment
- PHIPA breach risk assessment framework (Real Risk of Significant Harm analysis)
- Consent lifecycle management and audit trail requirements
- SOC 2 Type I readiness opinion writing for a healthcare SaaS context
- Clinical workflow analysis for security alert calibration
- PHI access revocation in a multi-tenant SaaS client relationship model

---

## Lessons Learned

**Policy-only controls fail in fast-moving engineering environments.** Three of the most serious findings in this engagement (ClinicalAI Corp pilot, alert muting, secondary use review bypass) all share the same root cause a control that exists in policy but has no technical enforcement. In healthcare, where the stakes of a breach are patient harm and IPC investigation, policy-only controls are insufficient. The lesson: every critical privacy control must have a system-level gate that cannot be bypassed without explicit approval.

**Healthcare SaaS companies inherit their clients' obligations.** CareSync is not just responsible for its own systems as an agent under PHIPA, it bears partial responsibility for what happens to PHI in its platform, even when client administrators make the mistake (deprovisioning failure, super user accounts). Understanding this shared responsibility model is essential for GRC work in Canadian health IT.

**The AI and PHI intersection is the fastest-moving risk in Canadian healthcare compliance.** The Ontario IPC's 2025 guidance on health data AI use, the anticipated CPPA provisions on secondary use, and the ClinicalAI Corp scenario in this project all point to the same emerging risk: engineering teams building AI features with PHI before governance frameworks are in place. A GRC practitioner who understands this risk and can help an organization get ahead of it is valuable in the current market.

---

## Related Projects

| Repository | Framework |
|---|---|
| [GRC-PCI-DSS-v4-MapleFinancial](../GRC-PCI-DSS-v4-MapleFinancial) | PCI-DSS v4.0 Canadian Regional Bank |
| [GRC-ISO27001-GovTech-Ontario](../GRC-ISO27001-GovTech-Ontario) | ISO 27001 Provincial Government Digital Services |
| [GRC-NIST-CSF-NovaSaaS](../GRC-NIST-CSF-NovaSaaS) | NIST CSF 2.0 Canadian B2B SaaS company |
| [GRC-PIA-PIPEDA-CanRetail](../GRC-PIA-PIPEDA-CanRetail) | PIA Canadian Retail Loyalty Program |

---

## About the Author

**Edem Messiga**
ISO 27001 Certified Lead Auditor | Cybersecurity GRC | Bilingual EN/FR
[linkedin.com/in/edem-messiga](https://linkedin.com/in/edem-messiga)

> All entities, individuals, patient records, regulatory findings, and systems in this project are entirely fictional and created for portfolio and professional development purposes only. No real patient data, organizations, or privacy incidents are represented.
