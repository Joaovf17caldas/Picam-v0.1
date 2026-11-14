# PICAM-PMM — PAM Maturity Questionnaire

**Applied in:** F1 (initial maturity) and F6 (reassessment)
**PICAM version:** 0.1 — public draft, under doctoral validation
**License:** CC BY 4.0

> **Draft wording.** The 21 indicators below follow the structure of the PICAM PAM Maturity Model (three indicators per PAM function, answered on a scale corresponding to levels L0 to L4). Final wording will be defined after exploratory interviews, expert review and pretesting. Do not use these items as a validated instrument.

## Instructions

1. Answer for the **environment in scope** (on-premises, cloud, or both, as defined in T-01).
2. For each indicator, choose the level (0–4) whose description best matches the **current, evidenced** situation. When in doubt between two levels, choose the lower one.
3. Record the evidence used (document, screenshot, report) in the "Evidence" column.
4. Compute the score per function (mean of its three indicators) and the overall level (see *Scoring*).

## Maturity levels

| Level | Name | Summary |
|---|---|---|
| L0 | Nonexistent | Shared, uncontrolled administrative accounts |
| L1 | Initial | Partial inventory; MFA on some accounts |
| L2 | Managed | Complete inventory; vault for critical credentials; MFA on all privileged access |
| L3 | Defined | Temporary elevation; periodic reviews; centralized and immutable logs; non-human identities inventoried |
| L4 | Optimized | Standing privileges eliminated; automated anomaly detection; risk-driven reviews; metrics tracked by leadership |

---

## 1. Discovery and inventory

| # | Indicator | 0 | 1 | 2 | 3 | 4 | Level | Evidence |
|---|---|---|---|---|---|---|---|---|
| 1.1 | Existence of a privileged account inventory | None | Informal / partial list | Complete for critical systems | Complete for all systems, with owners | Complete, automatically discovered and reconciled | | |
| 1.2 | Coverage of non-human identities | Not considered | A few known service accounts | Service accounts on critical systems | All service accounts, API keys and certificates | All non-human identities with owner and lifecycle | | |
| 1.3 | Update frequency | Never updated | Ad hoc | Annually | Quarterly or on every change | Continuous / automated | | |

## 2. Credential vaulting and rotation

| # | Indicator | 0 | 1 | 2 | 3 | 4 | Level | Evidence |
|---|---|---|---|---|---|---|---|---|
| 2.1 | Proportion of privileged credentials in a vault | None | < 25% | Critical credentials (≥ 50%) | ≥ 90% | 100%, with exceptions justified | | |
| 2.2 | Automatic rotation | No rotation | Manual, irregular | Manual, scheduled for critical credentials | Automatic for critical credentials | Automatic for all, including after each use where applicable | | |
| 2.3 | Absence of secrets in scripts and configuration files | Common, not tracked | Known in some places | Identified and being removed | Removed from critical systems; scanning in place | None; continuous secret scanning blocks new ones | | |

## 3. Temporary (just-in-time) elevation

| # | Indicator | 0 | 1 | 2 | 3 | 4 | Level | Evidence |
|---|---|---|---|---|---|---|---|---|
| 3.1 | Existence of on-demand elevation | None | Informal (password shared on request) | Available for some roles | Available for all privileged roles | Default and only path for elevated access | | |
| 3.2 | Approval requirement | None | Verbal | Recorded for critical systems | Recorded for all elevations, with justification | Risk-based approval, automated where low risk | | |
| 3.3 | Defined maximum duration | Not defined | Defined but not enforced | Enforced for some roles | Enforced for all roles | Enforced and tuned using usage data | | |

## 4. Elimination of standing privileges

| # | Indicator | 0 | 1 | 2 | 3 | 4 | Level | Evidence |
|---|---|---|---|---|---|---|---|---|
| 4.1 | Number of standing administrators | Unknown | Known, not controlled | Reduced on critical systems | Only emergency accounts and a minimal justified set | Only emergency accounts | | |
| 4.2 | Documented justification for standing privileges | None | For some | For all on critical systems | For all, reviewed periodically | For all, reviewed and time-bound | | |
| 4.3 | Downward trend | Not measured | Measured once | Measured, no clear trend | Decreasing over two consecutive reviews | Sustained at target (zero standing, except emergency) | | |

## 5. Strong authentication

| # | Indicator | 0 | 1 | 2 | 3 | 4 | Level | Evidence |
|---|---|---|---|---|---|---|---|---|
| 5.1 | MFA coverage on privileged accounts | None | Some accounts | All privileged human accounts | All privileged access, including management APIs and remote vendor access | All, with conditional/risk-based policies | | |
| 5.2 | Use of phishing-resistant methods | None | Piloted | For root / global administrators | For all privileged human accounts | For all privileged access where technically possible | | |
| 5.3 | Root / global administrator protection | Used daily, password only | MFA enabled | MFA, removed from daily use | Phishing-resistant MFA, removed from daily use, alert on use | Same as 3, plus tested emergency procedure and custody split | | |

## 6. Session monitoring and recording

| # | Indicator | 0 | 1 | 2 | 3 | 4 | Level | Evidence |
|---|---|---|---|---|---|---|---|---|
| 6.1 | Log centralization | Local logs only | Some systems centralized | Critical systems and control plane centralized | All privileged activity centralized | Centralized with automated correlation | | |
| 6.2 | Immutability | Logs can be altered by administrators | Restricted access | Write-once storage for critical logs | Immutable with defined retention for all privileged logs | Immutable, retention verified, integrity monitored | | |
| 6.3 | Recording or detailed logging of privileged sessions | None | On request | Critical systems | All privileged sessions, including vendor access | All, with automated anomaly detection | | |

## 7. Access review and segregation of duties

| # | Indicator | 0 | 1 | 2 | 3 | 4 | Level | Evidence |
|---|---|---|---|---|---|---|---|---|
| 7.1 | Review frequency | Never | Ad hoc | Annually | Quarterly with owner recertification | Risk-driven and event-triggered, plus quarterly | | |
| 7.2 | Evidence of revocations | None | Undocumented | Documented for some reviews | Documented for every review | Documented and tracked as a leadership metric | | |
| 7.3 | Segregation between administration, operations and audit | None | Informal | Defined; compensating controls for small teams | Enforced in the role model | Enforced and verified in each review | | |

---

## Scoring (draft)

1. **Function score** = mean of the three indicators of the function (0–4).
2. **Overall PICAM-PMM level** = the **lowest** function score, rounded down (a chain is as strong as its weakest link).
3. Report both the overall level and the seven function scores; the profile matters more than a single number.

> The scoring rule is provisional. The research design treats PAM maturity as a formative index; weighting and aggregation will be revised after validation.

## Summary sheet

| Function | Score (0–4) |
|---|---|
| 1. Discovery and inventory | |
| 2. Credential vaulting and rotation | |
| 3. Temporary elevation | |
| 4. Elimination of standing privileges | |
| 5. Strong authentication | |
| 6. Session monitoring and recording | |
| 7. Access review and segregation of duties | |
| **Overall PICAM-PMM level** | **L_** |

Applied by: ____________________ Date: __________ Phase: ☐ F1 ☐ F6
