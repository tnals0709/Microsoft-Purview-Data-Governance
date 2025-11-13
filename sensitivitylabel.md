# Microsoft Purview: Information Protection and Records Management

This guide documents the creation and deployment of robust Data Governance policies, demonstrating expertise in **Sensitivity Labeling (Data Security)**.

---

## 1. Sensitivity Label Implementation (Information Protection)

**Path:** `Purview` > `Information Protection` > `Sensitivity labels`

**Goal:** All documents are encrypted (confidential label). Only managers can remove the label from the document to decrypt via Purview Information Protection client. This setup is foundational to a Data Loss Prevention (DLP) strategy.

### A. Label: Confidential - Internal Only (General User Label)

| Setting Category | Configuration | Rationale |
| :--- | :--- | :--- |
| **Label Priority** | 0 | Highest priority for auto-labeling (dominant default security label). |
| **Description** | Confidential, internal use only. External sharing is restricted. Managers handle external sharing requests. | Clear security policy enforcement. |
| **Protection** | Control access (encryption) | **Mandatory Encryption** for all labeled data. |
| **Access Control** | Assigned to `[domain]` (organization) with **Owner permission**. | Allows general users to create, change, and delete their own labeled documents. |
| **Manager Rationale** | Removing/lowering the label requires the owner role, restricting general users from overriding the policy. |

### B. Label: Confidential - Manager Only (Decryption/Removal Label)

| Setting Category | Configuration | Rationale |
| :--- | :--- | :--- |
| **Label Priority** | 1 | Placed *below* the Internal Only label. |
| **Access Control** | Assigned to `managergroup@domain.com` with **Co-Owner permission**. | Grants managers the explicit right to remove or lower the label's classification (decryption). |
| **Requirement** | Requires a **mail-enabled security group** for permission assignment. | Ensures efficient management and verification of manager identity. |

### C. Publishing & Mandatory Policy

* **Published To:** Exchange email - All accounts
* **Default Document Label:** **Confidential - Internal Only**
* **Mandatory Labeling:** Users must provide justification to remove a label or lower its classification.
* **Goal:** Enforce a secure default posture and audit exceptions.

### D. Auto-labeling Policy: Confidential

* **Policy Name:** Document Auto-labeling policy - Confidential
* **File Extensions:** Configured to apply to a comprehensive list of Office and document file types (`.docx`, `.xlsx`, `.pdf`, etc.).
* **Locations:** Applied to **All SharePoint sites** and **all OneDrive accounts**.
* **Goal:** Automatically enforces the security label based on file type, scaling protection organization-wide.
