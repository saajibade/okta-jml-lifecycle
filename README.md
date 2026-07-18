# Okta JML Lifecycle Automation

I built an automated joiner-mover-leaver (JML) identity lifecycle in a free Okta organization, modeled on a fictional bank (Meridian Trust Bank). Access is never assigned to individuals: applications bind strictly to groups, attribute-driven group rules place people in those groups automatically based on their HR attributes, and the lifecycle runs itself. 

The standout moment of this project: changing a single department profile field dynamically revoked payment-system access and granted lending access automatically, generating an immutable audit log entry to prove it[cite: 1].

## What This Demonstrates
* **Role-Based Access Control (RBAC):** Applications are bound to functional groups rather than individual users to ensure scalability[cite: 1].
* **Attribute-Driven Group Rules:** Automated provisioning patterns modeled after real-world HR-driven lifecycle systems[cite: 1].
* **Full JML Lifecycle Automation:** Hands-free provisioning for new hires (Joiners), automatic access swaps for internal transfers (Movers) preventing privilege creep, and instant session termination for offboarding (Leavers)[cite: 1].
* **Identity-Layer Hardening:** Native MFA enrollment enforcement and robust, enterprise-grade password policies[cite: 1].
* **Least-Privilege Delegation:** Role-scoped administrator models ensuring helpdesk staff can support users without full infrastructure access[cite: 1].
* **Audit Readiness:** Full utilization of the Okta System Log to capture deterministic compliance evidence for every identity event[cite: 1].

## The Lifecycle, Evidenced
* **[Joiner](evidence/01-joiner):** User created with explicit role attributes; birthright and department-specific access appeared instantly without manual intervention[cite: 1].
* **[Mover](evidence/02-mover):** A single department attribute change cleanly revoked old permissions and granted new permissions simultaneously[cite: 1].
* **[Leaver](evidence/03-leaver):** Single-click deactivation instantly killed all active user sessions and blocked authentication, providing a timestamped audit trail[cite: 1].
* **[Hardening](evidence/04-hardening):** Global MFA enforcement, optimized password policies following modern NIST/NCSC frameworks, and a scoped helpdesk admin assignment[cite: 1].

## Operations
The comprehensive operating procedures, architecture overview, and design choices are fully detailed in the accompanying [JML Runbook (runbook.md)](runbook.md)[cite: 1].

## Honest Framing
This is a laboratory build deployed inside a free Okta Integrator organization utilizing a fictional banking scenario[cite: 1]. Bookmark applications are used as functional stand-ins for federated applications; while the downstream single sign-on (SAML/OIDC) plumbing is omitted, the underlying group assignment logic, rule evaluation engine, policy enforcement, and System Log audit trails are identical to a production Okta deployment[cite: 1]. In an enterprise setting, the attribute changes executed by hand would ingest automatically via an HR system integration over SCIM[cite: 1].

*<img width="766" height="340" alt="Step1-Environment-Provisioning" src="https://github.com/user-attachments/assets/4c2304e9-4fe4-4fbc-9b2f-53cd25408ba1" />
 *<img width="1091" height="535" alt="image" src="https://github.com/user-attachments/assets/f4e27199-6dfe-49d0-85a9-53ac7522370e" />
 <img width="565" height="336" alt="Step2-Policy and Access writing" src="https://github.com/user-attachments/assets/d76e5edd-f00d-4ae9-83fb-9480dbc30393" />

 *<img width="1022" height="515" alt="image" src="https://github.com/user-attachments/assets/ab8820e5-3d15-4f41-b4f1-323650423454" />
