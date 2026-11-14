# PICAM Manual — Overview of Phases and PAM Layer

**Version:** 0.1 — public draft, under doctoral validation
**Author:** João Victor Fernandes Caldas
**License:** CC BY 4.0

> This overview summarizes the structure of PICAM. Detailed Phase Guides (step-by-step instructions, worked examples based on a fictional reference company, and decision trees) are planned for later versions.

---

## 1. Formal definition

PICAM — Privileged Access Management Integrated Cloud Adoption Methodology — is a structured and documented set of guidelines, organized into sequential phases with decision gates, intended to lead medium-sized companies through the migration of data and systems to the cloud in a secure, controlled and sustainable way, with privileged access management as the integrating axis from the first phase. The methodology is vendor-agnostic and is designed to be applied autonomously by the company's own IT team or by a local IT service provider.

## 2. How to read this manual

- Each phase has: **Objectives**, **Activities**, **Deliverables**, **Security and PAM controls** and **Exit criteria**.
- At the end of each phase, the team holds a **gate review** and records one of three decisions: **proceed**, **proceed with conditions** (listing conditions, owner and deadline) or **remain in the phase**.
- Items are marked **mandatory**, **recommended** or **optional** (Principle 6 — Proportionality). In v0.1, only exit criteria are classified; full classification will follow.
- Template codes (T-01 … T-16) refer to the template catalog listed in Section 6.

## 3. Roles

| Role | Responsibility |
|---|---|
| Executive sponsor | Approves the business case, the policy and gate decisions |
| Adoption lead | Coordinates the phases and keeps the documentation |
| Privileged access owner | Named person accountable for privileged accounts, the policy and reviews |
| IT team / local IT provider | Executes activities; the provider may also act as compensating approver |
| Business manager | Approves elevations when the team has a single administrator (compensating control) |

The role model is designed for teams of two to fifteen people.

---

## 4. Phases

### F0 — Initiation and governance

**Objectives.** Establish the business justification for adoption, executive sponsorship, roles and the baseline of benefits and exposure against which success will be measured.

**Activities.**
- Prepare the business case with measurable objectives (total cost of ownership, availability, recovery time, provisioning agility, mobility and continuity).
- Appoint the executive sponsor, the adoption lead and the privileged access owner.
- Define the responsibility (RACI) matrix, including the service provider when applicable.
- Approve the Privileged Access Policy.
- Record the indicator baseline.
- Define risk appetite and budget, with a reserve for post-migration operating costs.

**Deliverables.** Project charter (T-01); business case (T-02); RACI matrix; Privileged Access Policy (T-04); indicator baseline (T-03).

**Security and PAM controls.** A formal policy defining what privileged access is, who may grant it, for how long and with what evidence; named designation of the privileged access owner; a segregation-of-duties rule suited to small teams — when there is a single administrator, approval of elevations is assigned to a business manager or to the service provider as a compensating control.

**Exit criteria (G0).** Sponsor formally appointed; business case approved; policy approved by leadership; baseline recorded with at least five benefit indicators and three exposure indicators.

### F1 — Assessment and privilege inventory

**Objectives.** Understand the current environment — systems, data, dependencies, regulatory obligations — and, as a priority, all accounts and credentials with elevated privileges, human and non-human, as well as the level of PAM maturity.

**Activities.**
- Inventory applications, servers, databases and SaaS services already in use, including unofficial ones (shadow IT).
- Map system dependencies.
- Classify data by sensitivity and identify applicable obligations (e.g., HIPAA, GLBA, PCI DSS, applicable state privacy laws).
- Discover privileged accounts — domain and local administrators, service accounts, shared accounts, remote vendor access (including to operational technology systems), keys and certificates.
- Apply the PICAM-PMM maturity questionnaire.
- Classify each workload by migration strategy (retain, retire, repurchase as SaaS, rehost, replatform, refactor).
- Record risks.

**Deliverables.** Workload inventory and data classification (T-06); Privileged Accounts and Credentials Inventory (T-05); PAM maturity report; risk register (T-11).

**Security and PAM controls.** Privilege discovery as a mandatory activity preceding any architecture decision; identification of credentials embedded in scripts, configuration files and scheduled tasks; identification of orphaned and former-employee accounts for immediate revocation as a quick win.

**Exit criteria (G1).** Inventory covering all systems classified as critical; every privileged account on critical systems associated with a named owner; identified orphaned accounts revoked or justified; initial PAM maturity recorded.

### F2 — Target architecture and privileged access model

**Objectives.** Select the provider or combination of providers and design the target architecture, with emphasis on the identity architecture and the privilege model that will apply in the cloud.

**Activities.**
- Apply the Vendor-Agnostic Provider Selection Matrix (T-07), with weighted criteria covering cost, regional presence, compliance, identity and logging capabilities, portability and local support.
- Define the exit strategy to mitigate lock-in.
- Design the organizational structure of accounts, subscriptions or projects and the landing zone.
- Define a single federated identity provider, with administrative identities separated from everyday identities.
- Define a tiered role model (organization administration, platform administration, operations, read-only and audit).
- Design approval-based temporary elevation, the emergency access procedure, the secret vaulting and rotation strategy, and the logging and alerting architecture.

**Deliverables.** Target architecture document; Privileged Access Model (T-08), with roles, scopes, maximum elevation durations and approvers; emergency access procedure (T-09); exit strategy.

**Security and PAM controls.** Prohibition of standing administrative accounts in the design, except emergency accounts; separation of duties between those who administer identities, those who administer workloads and those who audit; maximum durations for elevated sessions; workload identities instead of static keys wherever the platform allows.

**Exit criteria (G2).** Architecture approved by the sponsor; privileged access model reviewed by someone other than its author; every privileged role with defined scope, duration and approver; exit strategy documented.

### F3 — Secure foundation

**Objectives.** Deploy and verify the target environment before it receives any production workload, materializing the controls designed in F2.

**Activities.**
- Protect the root account or global administrator with phishing-resistant authentication and remove it from daily use.
- Create and test emergency accounts, with custodied credentials and automatic alerting on use.
- Federate the identity provider and require MFA for all administrative access.
- Deploy the secrets vault and automatic rotation.
- Centralize control-plane audit logs in immutable storage with defined retention.
- Apply preventive policies (guardrails) that block, for example, disabling logs or creating long-lived keys.
- Configure budget and anomalous-spend alerts.
- Run a configuration scan with a multicloud tool and compare results against secure configuration benchmarks (e.g., CIS Benchmarks).

**Deliverables.** Deployed foundation; configuration scan report; emergency access test record; completed Secure Foundation Checklist (T-10).

**Security and PAM controls.** Strong authentication on all privileged identities; no standing administrative privileges except emergency; temporary elevation operational and tested; immutable logging of every control-plane action; real-time alerting on use of emergency and root accounts.

**Exit criteria (G3).** All mandatory foundation checklist items met; emergency access test successful and documented; configuration scan with no open critical findings; no human identity with standing administrative privilege.

### F4 — Controlled migration in waves

**Objectives.** Migrate workloads in successive waves, starting with a low-criticality pilot wave, without carrying insecure credentials and practices from the source environment into the cloud.

**Activities.**
- Plan each wave with scope, window, rollback plan and acceptance criteria.
- For each workload, replace embedded credentials with vault references or workload identities.
- Create least-privilege service identities.
- Execute the migration, functional and performance tests and data validation.
- Scan code repositories and artifacts for exposed secrets.
- Revoke replaced credentials in the source environment.
- Decommission servers and accounts no longer needed.
- Record lessons learned from the wave.

**Deliverables.** Migration Wave Plan (T-12); validation report per wave; Credential Revocation Record (T-13); lessons learned.

**Security and PAM controls.** Prohibition of plaintext secrets at the destination; verified revocation of old credentials; non-human identities inventoried and with an owner; remote vendor access reconfigured to go through temporary elevation and session recording.

**Exit criteria (G4, per wave).** Acceptance tests passed; secret scan with no open findings; all privileged accounts in the wave under vault or temporary elevation; old credentials revoked; rollback plan formally decommissioned.

### F5 — Secure operations and privilege review

**Objectives.** Institutionalize operation of the cloud environment, ensuring that privilege controls are sustained over time and do not degrade for operational convenience.

**Activities.**
- Publish standard operating procedures (runbooks).
- Monitor privileged events and respond to alerts.
- Conduct quarterly privileged access reviews with recertification by owners.
- Maintain credential rotation.
- Periodically test the credential compromise response plan (T-15).
- Manage cost with FinOps practices (resource tagging, monthly reporting, removal of idle resources).
- Manage third-party and provider access with expiration dates.

**Deliverables.** Runbooks; access review reports (T-14); incident response exercise report; monthly cost reports.

**Security and PAM controls.** Periodic review with evidence; detection of grants made outside the process; automatic expiration of third-party access; any use of an emergency account treated as an incident requiring justification.

**Exit criteria (G5).** First access review cycle completed; credential compromise response exercise conducted; operating indicators being collected according to the baseline.

### F6 — Benefit measurement and continuous improvement

**Objectives.** Verify whether adoption delivered the benefits defined in F0, reassess PAM maturity and decide next steps.

**Activities.**
- Compare indicators against the baseline in a benefits realization review.
- Reapply the PICAM-PMM questionnaire.
- Consolidate lessons learned and update documentation.
- Define the roadmap for new waves or optimizations, returning to F1 for new workloads.

**Deliverables.** Benefits Realization Report (T-16); reassessed maturity report; updated roadmap.

**Security and PAM controls.** Target of advancing at least one PICAM-PMM level relative to F1; update of the Privileged Access Policy based on lessons learned.

**Exit criteria (G6).** Report presented to and accepted by the sponsor; decision recorded on the next cycle.

---

## 5. The cross-cutting PAM layer

PICAM treats PAM not as a final hardening step but as a layer that grows together with the migration. Seven PAM functions are activated, deepened or verified in each phase:

1. **Discovery and inventory** — knowing every privileged identity and credential, human and non-human.
2. **Credential vaulting and rotation** — privileged secrets kept in a vault and rotated automatically.
3. **Temporary (just-in-time) elevation** — privilege granted on request, with approval and a maximum duration.
4. **Elimination of standing privileges** — no permanent administrative rights, except controlled emergency accounts.
5. **Strong authentication** — MFA on all privileged access, phishing-resistant methods for the most critical identities.
6. **Session monitoring and recording** — centralized, immutable logs and recording or detailed logging of privileged sessions.
7. **Access review and segregation of duties** — periodic recertification and separation between administration, operations and audit.

### PAM integration matrix

D = designed · I = implemented · V = verified · M = maintained

| PAM function | F0 | F1 | F2 | F3 | F4 | F5 | F6 |
|---|---|---|---|---|---|---|---|
| Discovery and inventory | D | I | — | V | I | M | V |
| Credential vaulting and rotation | — | — | D | I | I | M | V |
| Temporary (just-in-time) elevation | — | — | D | I | V | M | V |
| Elimination of standing privileges | D | — | D | I | I | M | V |
| Strong authentication | D | — | D | I | V | M | V |
| Session monitoring and recording | — | — | D | I | I | M | V |
| Access review and segregation of duties | D | I | D | — | — | M | V |

## 6. PICAM PAM Maturity Model (PICAM-PMM)

| Level | Name | Description |
|---|---|---|
| L0 | Nonexistent | Shared, uncontrolled administrative accounts |
| L1 | Initial | Partial inventory; MFA on some accounts |
| L2 | Managed | Complete inventory; vault for critical credentials; MFA on all privileged access |
| L3 | Defined | Temporary elevation; periodic reviews; centralized and immutable logs; non-human identities inventoried |
| L4 | Optimized | Standing privileges eliminated; automated anomaly detection; risk-driven reviews; metrics tracked by leadership |

The questionnaire is in [`templates/PICAM-PMM-Questionnaire.md`](../templates/PICAM-PMM-Questionnaire.md).

## 7. Template catalog (planned for v1.0)

| Code | Template | Phase | Status in v0.1 |
|---|---|---|---|
| T-01 | Project charter | F0 | planned |
| T-02 | Business case | F0 | planned |
| T-03 | Indicator baseline | F0 | planned |
| T-04 | Privileged Access Policy | F0 | planned |
| T-05 | Privileged accounts and credentials inventory | F1 | **draft included** |
| T-06 | Workload inventory and data classification | F1 | planned |
| T-07 | Vendor-agnostic provider selection matrix | F2 | planned |
| T-08 | Privileged access model | F2 | planned |
| T-09 | Emergency access procedure | F2–F3 | planned |
| T-10 | Secure foundation checklist | F3 | planned |
| T-11 | Risk register | F1–F6 | planned |
| T-12 | Migration wave plan | F4 | planned |
| T-13 | Credential revocation record | F4 | planned |
| T-14 | Access review report | F5 | planned |
| T-15 | Credential compromise response playbook | F5 | planned |
| T-16 | Benefits realization report | F6 | planned |

## 8. Vendor neutrality note

The normative text of PICAM describes capabilities, not products. An informative cross-platform equivalence appendix (planned) will indicate, for each capability, examples of native features in the main providers and open-source alternatives. Such examples are illustrative and never prescriptive.
