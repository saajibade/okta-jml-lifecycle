# Okta JML Lifecycle Automation

I built an automated joiner-mover-leaver (JML) identity lifecycle in a free Okta organization, modeled on a fictional bank (Meridian Trust Bank). Access is never assigned to individuals: applications bind strictly to groups, attribute-driven group rules place people in those groups automatically based on their HR attributes, and the lifecycle runs itself. 

The standout moment of this project: changing a single department profile field dynamically revoked payment-system access and granted lending access automatically, generating an immutable audit log entry to prove it.

## What This Demonstrates
* **Role-Based Access Control (RBAC):** Applications are bound to functional groups rather than individual users to ensure scalability.
* **Attribute-Driven Group Rules:** Automated provisioning patterns modeled after real-world HR-driven lifecycle systems.
* **Full JML Lifecycle Automation:** Hands-free provisioning for new hires (Joiners), automatic access swaps for internal transfers (Movers) preventing privilege creep, and instant session termination for offboarding (Leavers).
* **Identity-Layer Hardening:** Native MFA enrollment enforcement and robust, enterprise-grade password policies.
* **Least-Privilege Delegation:** Role-scoped administrator models ensuring helpdesk staff can support users without full infrastructure access.
* **Audit Readiness:** Full utilization of the Okta System Log to capture deterministic compliance evidence for every identity event.

## The Lifecycle, Evidenced
* **[Joiner](evidence/01-joiner):** User created with explicit role attributes; birthright and department-specific access appeared instantly without manual intervention.
* **📸 Evidence Capture Checklist:**
* <img width="1091" height="535" alt="image" src="https://github.com/user-attachments/assets/f4e27199-6dfe-49d0-85a9-53ac7522370e" />


![Admin Dashboard](evidence/04-hardening/01_admin_dashboard.png)
* **[Mover](evidence/02-mover):** A single department attribute change cleanly revoked old permissions and granted new permissions simultaneously.
* **📸 Evidence Capture Checklist:**
* Take a screenshot of your complete **Groups List** displaying all four custom groups with zero manual users added yet.

![Empty Role Groups](evidence/01-joiner/01_empty_role_groups.png)
* **[Leaver](evidence/03-leaver):** Single-click deactivation instantly killed all active user sessions and blocked authentication, providing a timestamped audit trail.
* **[Hardening](evidence/04-hardening):** Global MFA enforcement, optimized password policies following modern NIST/NCSC frameworks, and a scoped helpdesk admin assignment.

## Operations
The comprehensive operating procedures, architecture overview, and design choices are fully detailed in the accompanying [JML Runbook (runbook.md)](runbook.md).

## Honest Framing
This is a laboratory build deployed inside a free Okta Integrator organization utilizing a fictional banking scenario. Bookmark applications are used as functional stand-ins for federated applications; while the downstream single sign-on (SAML/OIDC) plumbing is omitted, the underlying group assignment logic, rule evaluation engine, policy enforcement, and System Log audit trails are identical to a production Okta deployment. In an enterprise setting, the attribute changes executed by hand would ingest automatically via an HR system integration over SCIM. 
