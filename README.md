# Microsoft Purview: Data Governance and Compliance

This repository documents the implementation of enterprise-level **Microsoft Purview** policies, demonstrating expertise in **Information Protection (Data Security)** and **Records Management (Compliance)**.

This work ensures corporate data meets regulatory requirements and enforces critical controls over sensitive content lifecycle across Microsoft 365 services (SharePoint, OneDrive, Exchange, Teams).

---

## Key Project Components

| Project Component | Technology Used | Skill Demonstrated |
| :--- | :--- | :--- |
| **Data Classification & Encryption** | Sensitivity Labels | Enforcing encryption and access control based on content sensitivity. |
| **Records Management** | Retention Labels & Adaptive Scopes | Implementing compliance-mandated data retention (e.g., 7 years) and secure disposal. |
| **Access Control** | Ownership Delegation & Policy Justification | Structuring permissions to delegate decryption rights to managers while maintaining audit trails. |
| **Automation** | Auto-labeling Policies | Scaling security policies across SharePoint and OneDrive without relying on manual user action. |

---

## 1. Sensitivity Label Implementation (Information Protection)

This configuration establishes two sensitivity labels to enforce encryption and tight access control, aligning with Data Loss Prevention (DLP) goals.

* **Goal:** Restrict external sharing and prevent unauthorized decryption.
* **Method:** Two labels (`Confidential - Internal Only` and `Confidential - Manager Only`) were created to allow managers to remove or lower the label's classification (decryption) by granting them **Co-Owner permission** via a designated security group.
* **Security Posture:** Implemented **mandatory labeling** and a default classification level for all new documents, preventing unsecured data creation.

---

## 2. Retention Policy Implementation (Records Management)

This configuration ensures mandatory data preservation for compliance and business continuity purposes.

* **Goal:** Retain all corporate data for **7 years** to meet regulatory requirements, even if the user attempts deletion.
* **Preservation Method:** Defined a Retention Label that moves deleted content to the **Preservation Hold Library**, making it inaccessible to end-users but available for audit.
* **Targeting Method:** Utilized **Adaptive Scopes** for SharePoint sites to dynamically apply the retention policy to all existing and future team sites, ensuring future-proof coverage.
