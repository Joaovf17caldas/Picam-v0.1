# PICAM ↔ NIST CSF 2.0 / NIST SP 800-53 Rev. 5 — Crosswalk (DRAFT)

**PICAM version:** 0.1 — public draft, under doctoral validation
**License:** CC BY 4.0

> **Draft status.** This is an initial, informative mapping prepared by the author. It has not been reviewed by NIST or by independent experts and will be revised. A mapping indicates that a PICAM element *contributes to* the referenced outcome or control; it does not claim full coverage or compliance.

**References**
- NIST. *The NIST Cybersecurity Framework (CSF) 2.0*. NIST CSWP 29, 2024. DOI: 10.6028/NIST.CSWP.29
- NIST. *Security and Privacy Controls for Information Systems and Organizations*. SP 800-53 Rev. 5, 2020. DOI: 10.6028/NIST.SP.800-53r5

## 1. Phase-level mapping

| PICAM phase | Main CSF 2.0 Functions | CSF 2.0 Categories / Subcategories (examples) | SP 800-53 Rev. 5 (examples) |
|---|---|---|---|
| F0 — Initiation and governance | GOVERN | GV.OC-03 (legal/regulatory requirements); GV.RM-01, GV.RM-02 (risk objectives, risk appetite); GV.RR-02 (roles and authorities); GV.PO-01 (policy) | PM-9, PL-2, AC-1, AC-5 |
| F1 — Assessment and privilege inventory | IDENTIFY | ID.AM-01, ID.AM-02 (hardware, software and services inventories); ID.AM-03 (data flows); ID.AM-05 (prioritization); ID.AM-07 (data inventories); ID.RA (risk assessment) | CM-8, RA-2, RA-3, AC-2, IA-4 |
| F2 — Target architecture and access model | GOVERN, PROTECT | GV.SC (supplier/provider risk); PR.AA-01 (identities and credentials managed); PR.AA-05 (access permissions, least privilege, separation of duties) | AC-5, AC-6, SA-9, SA-8, IA-2 |
| F3 — Secure foundation | PROTECT, DETECT | PR.AA-03 (authentication); PR.PS-01 (configuration management); PR.PS-04 (log records); PR.DS-01 (data at rest); DE.CM (continuous monitoring) | IA-2(1), IA-2(2), AC-6(5), AU-2, AU-9, CM-6, CM-7 |
| F4 — Controlled migration in waves | PROTECT | PR.AA-01 (credential lifecycle); PR.AA-05 (least privilege for service identities); PR.DS-02 (data in transit); PR.PS-02 (software maintenance) | IA-5, AC-2(3), AC-6, SC-8, SC-28 |
| F5 — Secure operations and privilege review | DETECT, RESPOND, PROTECT | DE.CM-03 (personnel activity monitored); DE.CM-06 (external service provider activity monitored); DE.AE (adverse event analysis); RS.MA (incident management); PR.AA-05 (access review) | AC-2(3), AC-6(7), AU-6, IR-4, IR-3, PS-7 |
| F6 — Benefit measurement and continuous improvement | GOVERN, IDENTIFY | GV.OV (oversight); ID.IM (improvement) | CA-7, PM-6, PM-14 |

## 2. PAM function mapping

| PICAM PAM function | CSF 2.0 (examples) | SP 800-53 Rev. 5 (examples) |
|---|---|---|
| Discovery and inventory | ID.AM, PR.AA-01 | CM-8, AC-2, IA-4 |
| Credential vaulting and rotation | PR.AA-01, PR.DS-01 | IA-5, IA-5(1), SC-12, SC-28 |
| Temporary (just-in-time) elevation | PR.AA-05 | AC-2(2), AC-6, AC-6(1) |
| Elimination of standing privileges | PR.AA-05 | AC-6, AC-6(2), AC-6(5) |
| Strong authentication | PR.AA-03 | IA-2, IA-2(1), IA-2(2), IA-2(8) |
| Session monitoring and recording | PR.PS-04, DE.CM-03 | AU-2, AU-6, AU-9, AU-12, AU-14 |
| Access review and segregation of duties | PR.AA-05, GV.RR | AC-2(3), AC-5, AC-6(7) |

## 3. Gate exit criteria mapping (G0, G1)

| Exit criterion | CSF 2.0 | SP 800-53 Rev. 5 |
|---|---|---|
| G0 — Sponsor formally appointed | GV.RR-01, GV.RR-02 | PM-2 |
| G0 — Business case approved | GV.RM-01 | PM-9 |
| G0 — Privileged Access Policy approved by leadership | GV.PO-01 | AC-1, IA-1 |
| G0 — Baseline with ≥ 5 benefit and ≥ 3 exposure indicators | GV.OV, ID.IM | PM-6 |
| G1 — Inventory covering all critical systems | ID.AM-01, ID.AM-02, ID.AM-05 | CM-8, RA-2 |
| G1 — Every privileged account on critical systems with a named owner | PR.AA-01 | AC-2, IA-4 |
| G1 — Orphaned accounts revoked or justified | PR.AA-01, PR.AA-05 | AC-2(3), PS-4 |
| G1 — Initial PAM maturity recorded | ID.RA, ID.IM | CA-2 |

## 4. Open items for later versions

- Verify each subcategory identifier and wording against the official CSF 2.0 reference tool.
- Extend gate-level mapping to G2–G6.
- Add mapping to ISO/IEC 27001:2022 Annex A / ISO/IEC 27002:2022, CIS Controls v8 and the CSA Cloud Controls Matrix.
- Submit the crosswalk to the expert panel for review.
