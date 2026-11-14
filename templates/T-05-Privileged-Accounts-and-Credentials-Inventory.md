# T-05 — Privileged Accounts and Credentials Inventory

**Phase:** F1 (updated in F4 and verified in F3, F6)
**PICAM version:** 0.1 — public draft, under doctoral validation
**License:** CC BY 4.0
**Spreadsheet version:** [`T-05-Privileged-Accounts-Inventory.csv`](T-05-Privileged-Accounts-Inventory.csv)

> ⚠️ **Never record passwords, keys, tokens or any secret value in this inventory.** Record only an internal identifier and where the credential is stored.

## Purpose

Each row corresponds to an identity or credential with elevated privilege. The inventory covers **human and non-human identities equally** (Principle 4).

## Fields

| Field | Description | Allowed values / format | Example entry |
|---|---|---|---|
| Identifier | Internal code, never the password or key | `PRV-NNNN` | PRV-0042 |
| Type | Kind of identity or credential | Named human · Shared human · Service · Application · API key · Certificate · Vendor access | Service account |
| System or platform | Where the privilege is exercised | Free text | ERP — database server |
| Privilege level | Level of elevated right | Global administrator · System administrator · Operator · Privileged read | Database administrator |
| Owner | Named responsible person | Person or role holder | IT manager |
| Use | Documented purpose | Free text | Nightly integration with tax system |
| Current storage | Where the credential lives today | Vault · File · Script · Spreadsheet · Memory | Embedded in scheduled script |
| Authentication | Authentication method | Password · MFA · Phishing-resistant MFA · Workload identity | Static password |
| Last rotation | Date of last rotation | YYYY-MM-DD or "Unknown" | Unknown |
| Criticality | Impact if compromised | High · Medium · Low | High |
| Migration action | What happens to it in the migration | Eliminate · Replace with workload identity · Move to vault · Keep with justification | Replace with workload identity |
| Status | Progress of the migration action | Pending · In progress · Completed | Pending |

## Completion instructions

1. Start with critical systems identified in T-06.
2. For each system, list domain/local administrators, shared accounts, service accounts, application accounts, API keys, certificates and remote vendor access.
3. Search scripts, configuration files and scheduled tasks for embedded credentials; record the **location** in "Current storage", never the value.
4. Assign a named **Owner** to every row on a critical system (mandatory for gate G1).
5. Flag orphaned and former-employee accounts; revoke them or record a justification.
6. Update "Status" during F4 as each wave is migrated.

## Example (fictional reference company)

| Identifier | Type | System or platform | Privilege level | Owner | Use | Current storage | Authentication | Last rotation | Criticality | Migration action | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRV-0042 | Service | ERP — database server | Database administrator | IT manager | Nightly integration with tax system | Embedded in scheduled script | Static password | Unknown | High | Replace with workload identity | Pending |
