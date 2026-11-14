# PICAM — Privileged Access Management Integrated Cloud Adoption Methodology

> **Status: v0.1 — public draft, under doctoral validation.**
> This is an early working draft. PICAM has **not** yet been validated. Its content validation (Delphi expert panel) and field evaluation (multiple-case study) are the object of ongoing doctoral research. Content will change between versions.

**Author:** João Victor Fernandes Caldas
**License:** [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE)
**How to cite:** see [`CITATION.cff`](CITATION.cff)

---

## What PICAM is

PICAM is a structured and documented set of guidelines, organized into sequential phases with decision gates, intended to lead **medium-sized companies** through the migration of data and systems to the cloud in a secure, controlled and sustainable way, with **Privileged Access Management (PAM) as the integrating axis from the first phase**.

PICAM is:

- **Documented** — manual, phase guides, gate checklists and templates, all written down.
- **Vendor-agnostic** — every activity is described in terms of capability and expected outcome, never in terms of a proprietary service. It can be applied regardless of the cloud provider chosen.
- **Phase-structured** — seven sequential phases (F0–F6), each closed by a verifiable decision gate (G0–G6).
- **Autonomous** — designed to be applied by a company's own IT team or by a local IT service provider, without the physical presence or ongoing consulting of its author.

PICAM is the methodological artifact of the doctoral research project *"The Benefits Obtained from the Inclusion of Cloud Computing in Medium-Sized Companies"*, conducted under the Design Science Research paradigm. The empirical testbed is medium-sized companies in Texas, New Mexico, Oklahoma, Kansas, Nebraska, Wyoming, Montana and Idaho; the methodology itself is designed for nationwide application.

## The eight principles

1. **Identity as the perimeter.** The migration sequence is guided by the maturity of privileged identity control, not only by the technical readiness of workloads.
2. **Minimal, temporary and justified privilege.** Elevated access is granted at the smallest scope, for the shortest time and upon recorded justification, aiming at zero standing privileges (except controlled emergency accounts).
3. **No migration without a foundation.** No production workload is migrated before the secure foundation — federated identity, tested emergency accounts, credential vault and immutable logs — is completed and verified.
4. **Humans and machines with equal rigor.** Non-human identities (service accounts, workload roles, API keys, automation tokens) are inventoried, protected and reviewed like human administrators.
5. **Vendor neutrality.** Capabilities and outcomes, never proprietary services; cross-platform equivalences are informative only.
6. **Proportionality.** Controls and deliverables are scaled to data criticality and team size; mandatory, recommended and optional items are always explicit.
7. **Evidence and measurement.** Each phase produces verifiable evidence and feeds the benefit and exposure indicators defined in the baseline.
8. **Autonomy through documentation.** Every step has a written instruction, a completion criterion and a worked example.

## The seven phases

| Phase | Name | Question it answers | Gate |
|---|---|---|---|
| F0 | Initiation and governance | Why migrate, who decides and how will we know it was worth it? | G0 |
| F1 | Assessment and privilege inventory | What do we have, who has privileged access to what and what is our maturity? | G1 |
| F2 | Target architecture and access model | Where are we going and how will privilege work at the destination? | G2 |
| F3 | Secure foundation | Is the target environment ready and protected before receiving data? | G3 |
| F4 | Controlled migration in waves | How do we migrate each workload without carrying insecure credentials? | G4 (per wave) |
| F5 | Secure operations and privilege review | How do we maintain control day to day? | G5 |
| F6 | Benefit measurement and continuous improvement | Did the cloud deliver what was promised, and what should improve? | G6 → F1 |

F4 repeats for each migration wave; F6 leads back to F1 whenever new workloads are considered.

## Architecture in three layers

- **Phase layer** — F0 to F6 with gates G0 to G6.
- **Cross-cutting PAM layer** — seven functions: discovery and inventory; credential vaulting and rotation; temporary (just-in-time) elevation; elimination of standing privileges; strong authentication; session monitoring and recording; access review and segregation of duties.
- **Governance and measurement layer** — roles and responsibilities matrix, Privileged Access Policy, risk register, benefits baseline and the **PICAM PAM Maturity Model (PICAM-PMM)**, levels L0 (nonexistent) to L4 (optimized).

## Repository contents (v0.1)

| Path | Content |
|---|---|
| [`manual/`](manual/) | Overview of phases F0–F6 and of the PAM layer |
| [`checklists/`](checklists/) | Gate checklists G0 and G1 (Initiation and Assessment) |
| [`templates/`](templates/) | T-05 Privileged Accounts and Credentials Inventory; PICAM-PMM maturity questionnaire |
| [`crosswalk/`](crosswalk/) | Draft mapping of PICAM phases and controls to NIST CSF 2.0 and NIST SP 800-53 Rev. 5 |
| [`CHANGELOG.md`](CHANGELOG.md) | Version history |

The full documentation package planned for v1.0 contains the Manual, seven Phase Guides, seven Gate Checklists and sixteen templates (T-01 to T-16). See the [roadmap in the changelog](CHANGELOG.md).

## Disclaimer

This draft is provided "as is", for review and research purposes. It is not a certification scheme, does not replace professional judgment, and does not imply endorsement by any cloud provider, standards body or institution. Mentions of standards (NIST, ISO/IEC, CIS, CSA) refer to publicly available documents and do not imply affiliation.

## Feedback

Comments and suggestions are welcome through GitHub Issues. Please do not post confidential information about any organization.
