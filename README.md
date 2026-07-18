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
 <img width="604" height="233" alt="image" src="https://github.com/user-attachments/assets/375195f7-0582-43a8-8c1e-d1a38e4b6bed" />
 <img width="1037" height="587" alt="image" src="https://github.com/user-attachments/assets/13d6f161-c2b6-49d2-8f4b-a56f1c6a57a7" />

<img width="625" height="239" alt="image" src="https://github.com/user-attachments/assets/9385fcc7-4c9a-4cbc-afb4-12551fc45600" />

<img width="1073" height="455" alt="image" src="https://github.com/user-attachments/assets/327198e8-9f19-49e0-b52d-e8032bc47eb3" />
<img width="647" height="397" alt="image" src="https://github.com/user-attachments/assets/1d6fad4e-57e4-41a6-8e58-d02e800ca181" />

<img width="1097" height="535" alt="image" src="https://github.com/user-attachments/assets/ee34562d-21f0-4641-a7fd-c95cc821ab62" />
<img width="615" height="308" alt="image" src="https://github.com/user-attachments/assets/717e34b7-4ec3-4c37-956e-02d8846421e1" />

<img width="1030" height="538" alt="image" src="https://github.com/user-attachments/assets/99788af6-1100-4176-a944-bf28c18f5078" />

<img width="555" height="233" alt="Step7-executing-the-mover-phase" src="https://github.com/user-attachments/assets/ff05ef09-ae8e-4c3f-9885-a13137b042dc" />

<img width="596" height="297" alt="Step8-executing-the-leaver-phase" src="https://github.com/user-attachments/assets/17bfd955-777b-4028-935a-6e4ba157c349" />

<img width="787" height="516" alt="leaver" src="https://github.com/user-attachments/assets/52cd9ed3-c615-4dd2-9713-06ca998728a4" />


