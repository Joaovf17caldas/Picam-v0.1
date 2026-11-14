# Gate Checklist G1 — Assessment and Privilege Inventory (Phase F1)

**PICAM version:** 0.1 — public draft, under doctoral validation
**License:** CC BY 4.0

| Field | Value |
|---|---|
| Company (code, not name, if shared) | |
| Gate review date | |
| Participants | |
| Privileged access owner | |

## Instructions

1. Check each item only if the **evidence** listed exists and can be shown.
2. Every item marked **[M] mandatory** must be met to record the decision "proceed".
3. Items marked **[R] recommended** may be left open with a justification.
4. Never record passwords, keys or secrets in this checklist or in any template.

## A. Environment inventory

- [ ] **[M]** Workload inventory covers **all systems classified as critical** — *Evidence: T-06.*
- [ ] **[M]** Data classified by sensitivity for each critical system — *Evidence: T-06.*
- [ ] **[M]** Applicable obligations identified (sector regulations such as HIPAA, GLBA, PCI DSS; applicable state privacy laws) — *Evidence: T-06.*
- [ ] **[R]** SaaS services and unofficial tools (shadow IT) identified.
- [ ] **[R]** System dependencies mapped.
- [ ] **[R]** Migration strategy assigned to each workload (retain, retire, repurchase, rehost, replatform, refactor).

## B. Privilege discovery

- [ ] **[M]** Privilege discovery completed **before** any architecture decision — *Evidence: T-05 dated before F2 starts.*
- [ ] **[M]** Inventory includes human identities: domain administrators, local administrators, shared administrative accounts — *Evidence: T-05.*
- [ ] **[M]** Inventory includes non-human identities: service accounts, application accounts, API keys, certificates — *Evidence: T-05.*
- [ ] **[M]** Remote vendor access identified, including access to operational technology systems where applicable — *Evidence: T-05.*
- [ ] **[M]** **Every privileged account on critical systems is associated with a named owner** — *Evidence: T-05 "Owner" column complete for critical rows.*
- [ ] **[R]** Credentials embedded in scripts, configuration files and scheduled tasks identified and recorded (location only, never the secret).

## C. Quick wins

- [ ] **[M]** Orphaned and former-employee accounts identified — *Evidence: T-05 rows flagged.*
- [ ] **[M]** Each identified orphaned account **revoked or justified in writing** — *Evidence: revocation record or justification signed by the privileged access owner.*

## D. Maturity and risk

- [ ] **[M]** PICAM-PMM questionnaire applied and **initial PAM maturity level recorded** — *Evidence: PAM maturity report.*
- [ ] **[M]** Risk register created with the risks identified in F1 — *Evidence: T-11.*
- [ ] **[R]** Exposure indicators of the baseline (T-03) updated with inventory data.

## Gate decision

| Decision | Mark one |
|---|---|
| Proceed to F2 | ☐ |
| Proceed with conditions | ☐ |
| Remain in F1 | ☐ |

**Initial PICAM-PMM level recorded:** L__

**Conditions (if any), owner and deadline:**

| Condition | Owner | Deadline |
|---|---|---|
| | | |

**Sponsor approval:** ____________________ **Date:** __________
