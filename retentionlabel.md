## 2. Retention Policy Implementation (Records Management)

**Path:** `Purview` > `Records Management`

**Goal:** Ensure compliance and robust data governance by retaining corporate data for 7 years and securely disposing of it afterwards.

### Retention Label Definition

**Description:** To ensure compliance and robust data governance, our Microsoft Purview Retention Labels are configured to retain company data for 7 years. This means that even if a user 'deletes' an item from their visible Microsoft 365 interface, a secure copy is automatically moved to the hidden **Preservation Hold Library**. This preserved content remains inaccessible to the end-users but is retained for the full 7-year duration, fulfilling our critical compliance requirements. Furthermore, these Retention Labels significantly benefit the IT team by aiding in recovery from accidental removals, facilitating data rollback, and providing a crucial layer of protection in various disaster scenarios.

| Setting Category | Configuration | Compliance Goal |
| :--- | :--- | :--- |
| **Retention Period**| **7 years** | Meets critical regulatory requirements. |
| **During Retention**| Retain items even if users delete | Content is moved to the **Preservation Hold Library** to prevent permanent deletion by end-users. |
| **After Retention**| Delete items automatically | Ensures secure disposal after the compliance period is met. |

### Adaptive Scope Configuration

Adaptive Scopes are used for precise, dynamic targeting of retention policies across large organizations.

**Path:** `Purview` > `Settings` > `Roles and scopes` > `Adaptive scopes` > `Create scope`

* **Name:** Scope - SharePoint Sites
* **Scope:** SharePoint sites
* **Simple Query:** `Site URL starts with https://tenant.sharepoint.com/sites;`
    * *Goal:* Dynamically scopes all existing and future SharePoint communication and team sites.

### Publish Auto-Retention Labels

Two separate auto-retention policies are published to ensure comprehensive coverage across both static and adaptive locations.

| Policy Name | Scope Type | Locations | Applied To Content |
| :--- | :--- | :--- | :--- |
| **Auto-retention label for OneDrive** | Static | Exchange email, Microsoft 365 Group sites, **OneDrive accounts**, SharePoint classic and communication sites. | Cloud attachments and links shared in Exchange, Teams, Viva Engage, and Copilot. |
| **Auto-retention label for SharePoint sites** | Adaptive | **SharePoint Sites** (using the new Adaptive Scope). | Cloud attachments and links shared in Exchange, Teams, Viva Engage, and Copilot. |

---

### Recovery Link Examples

These links illustrate where content is held within the Preservation Hold Library:

* **OneDrive Recovery Link Example:** `https://tenant-my.sharepoint.com/personal/email_domain_com/PreservationHoldLibrary/Forms/AllItems.aspx`
* **SharePoint Site Recovery Link Example:** `https://tenant.sharepoint.com/sites/sitename/PreservationHoldLibrary`
