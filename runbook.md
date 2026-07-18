# Identity Lifecycle Runbook: Meridian Trust Bank (Okta)

## Design Principles
* **Group-Based Assignment Only:** Applications are wired strictly to groups, never to individual users, to prevent privilege creep and ensure clean automation.
* **Attribute-Driven Membership:** Group memberships are dynamically computed based on identity attributes (e.g., Department) instead of being manually assigned by IT admins.
* **Least-Privilege Admin:** Administrative access is restricted based on functional roles; helpdesk personnel are given only the specific access required to manage users and credentials without full configuration rights.

## Joiner
* **Trigger:** A new employee is hired and added to the HR system (simulated via manual creation in the Okta directory).
* **Operator:** IAM Administrator.
* **Required Attributes:** First Name, Last Name, Username/Email, and Department (e.g., "Lending" or "Payments").
* **Automated Actions:** The system evaluates the Department attribute, automatically adds the user to the corresponding role group (`Dept-Lending` or `Dept-Payments`), assigns birthright access (`All-Staff`), and provisions the relevant application tiles to the user's dashboard.
* **Evidence Produced:** System Log events capturing user creation, dynamic group membership additions by rules, and subsequent application assignments.

## Mover
* **Trigger:** An employee transfers departments within the bank.
* **Operator:** IAM Administrator or HR data sync.
* **Action:** A single update to the user's `Department` attribute profile field.
* **Automated Actions:** The system automatically re-evaluates the group rules, removes the user from the old department group (revoking old access tiles), and adds them to the new department group (granting new access tiles), while safely maintaining their birthright access.
* **Evidence Produced:** System Log records documenting group membership removal by rule, group membership addition by rule, application revocation, and new application assignment.

## Leaver
* **Trigger:** An employee separates from the organization.
* **Operator:** Security Operations or IAM Team.
* **Action:** Explicit account deactivation (`More Actions -> Deactivate`).
* **Reasoning:** Deactivation terminates all active sessions, blocks authentication, and removes access immediately while preserving the account identity and logs for future audit compliance. Suspend is only used for temporary absences (e.g., leave of absence) where access needs a clean return.
* **Evidence Produced:** Failed login attempt logs, a status update showing `Deactivated` in the directory, and a definitive System Log deactivation timestamp bound to the executing admin.

## Authentication Policy
* **MFA Enrollment:** Okta Verify enrollment is marked as **Required** in the enrollment policy, ensuring multi-factor challenges protect all integrated applications natively at the identity layer.
* **Password Policy:** Hardened to a minimum length of 12+ characters, requiring uppercase, lowercase, numbers, and a common-password blocklist check with account lockout enforced after 10 failed attempts.
* **Design Decision:** Forced periodic password expiry is deliberately **disabled** following current NCSC and NIST guidelines, as routine expiry drives users to use predictable patterns or reuse passwords, whereas complexity, MFA, and lockout provide robust security.

## Admin Model
* **Super Administrators:** Restricted to primary IAM infrastructure engineering accounts only.
* **Help Desk Administrators:** Scoped strictly to the standard Help Desk Administrator role. They possess permissions to look up users, unlock accounts, and reset passwords or authentication factors, but have zero access to alter security policies, modify applications, or adjust group rules.

## Lab Shortcuts vs. Production
* **Admin-Set Passwords:** Used in this lab environment to easily test dashboard access with fake email domains; in a production environment, this would be replaced by automated Okta activation emails or secure onboarding registration flows.
* **Bookmark Apps:** Used as functional visual stand-ins to verify dashboard assignment behavior; in production, these would be built out using full SAML or OIDC single sign-on federation configurations.
* **Manual Attribute Edits:** Department values were modified by hand in this lab; in production, these attribute shifts would be pushed directly into Okta via automated HR system integrations (such as Workday or BambooHR) using SCIM.
