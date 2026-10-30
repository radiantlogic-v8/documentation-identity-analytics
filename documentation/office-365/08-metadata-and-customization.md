---
title: "Office 365 - Metadata and customization"
description: "Office 365 - Metadata and customization"
---

# Metadata and customization

This page describes the Office 365 metadata and the ways to customize the Office 365 pages and reviews.

## Metadata

Four metadata compute access counters for SharePoint Online and Exchange Online. They are computed before the rules, only when `isOffice365Active` is `true`, and their values are available as extended attributes:

| **Metadata**         | **Entity**  | **Extended attributes**                                                                                                                              |
| :------------------- | :---------- | :--------------------------------------------------------------------------------------------------------------------------------------------------- |
| `spo_sitemetrics`    | Application | `spo_sitemetrics_nbreadaccess`, `spo_sitemetrics_nbwriteaccess`, `spo_sitemetrics_nbfullcontrolaccess`                                              |
| `eol_mailboxmetrics` | Application | `eol_mailboxmetrics_nbreadaccess`, `eol_mailboxmetrics_nbwriteaccess`, `eol_mailboxmetrics_nbfullcontrolaccess`, `eol_mailboxmetrics_nbviewaccess`, `eol_mailboxmetrics_nbdelegation` |
| `spo_foldermetrics`  | Permission  | `spo_foldermetrics_nbreadaccess`, `spo_foldermetrics_nbwriteaccess`, `spo_foldermetrics_nbfullcontrolaccess`                                        |
| `eol_foldermetrics`  | Permission  | `eol_foldermetrics_nbreadaccess`, `eol_foldermetrics_nbwriteaccess`, `eol_foldermetrics_nbfullcontrolaccess`, `eol_foldermetrics_nbviewaccess`      |

The permission metadata (`spo_foldermetrics`, `eol_foldermetrics`) are embedded in rules, so you can use their values in your own rules. For the letters counted by each value, see [Counters](./05-acl-and-rights/#counters).

On the share and folder details pages and on the SharePoint Online and Exchange Online search pages, the **Number of Read Access**, **Number of Write Access** and **Number of Full Control Access** KPIs use these metadata; for the other families they use the standard `bwa_applicationanalytics` and `bwa_permissionanalytics` metadata.

### Attributes

The following attributes complete the list of attributes described in [Available Metadata](../identity-analytics/integration-guide/05-metadata):

- **Attribute Name:** `nbviewaccess`
- **Description:** nb view access (Exchange Online mailboxes and mailbox folders, computed by the `eol_mailboxmetrics` and `eol_foldermetrics` metadata)
- **Entity:** Application, Permission

---

- **Attribute Name:** `nbdelegation`
- **Description:** nb delegation (Exchange Online mailboxes, computed by the `eol_mailboxmetrics` metadata)
- **Entity:** Application

---

> **Note** For SharePoint Online and Exchange Online, `nbreadaccess`, `nbwriteaccess` and `nbfullcontrolaccess` are computed from the rights of each workload by the `spo_sitemetrics` and `eol_mailboxmetrics` metadata (sites and mailboxes) and by the `spo_foldermetrics` and `eol_foldermetrics` metadata (lists, folders and mailbox folders), when the configuration variable `isOffice365Active` is `true`. For Exchange Online mailboxes, `nbfolder` and `nbmanagedfolder` don’t count the mailbox root (*Top of Information Store*) and the pseudo-folder `/$BW_MAIL_BOX_RIGHTS$` that holds the mailbox delegations.

## Customization

### Unstructured data reviews: custom folder right mapping

In an unstructured data review, the rights are displayed to the reviewers as they are collected, for example `YVWXZ012UT45QKEFGBJCHAIMDSPON3RL` for a SharePoint Online ACL, which isn’t readable. The **Custom Folder Right Mapping** section of the review campaign wizard lets you provide a script, through the **Edit Mapping** button, that translates each right into a readable label. In the **Edit Custom Folder Right Mapping Script** window, you can start from the default script or an existing one, then save it with **Override existing script** or **Create new script**.

The script is evaluated for each right by the business view script `unstructureddatareviewbv.javascript` (function `updateRightActionDisplayName`, `/views/bw_access360/searchanalytics/unstructureddata/`), for the review and for the campaign reports. The value of the last expression evaluated is displayed to the reviewer; if the script returns nothing, the raw right is displayed. The following variables are available:

| **Variable**        | **Content**                                                                                         |
| :------------------ | :-------------------------------------------------------------------------------------------------- |
| `folderrightaction` | The right to translate: the collected rights letters, as one string                                 |
| `applicationfamily` | The family of the share, for example `SharePointOnline`, `ExchangeOnline` or `OneDrive`             |
| `applicationtype`   | The type of the share, for example `Filesystem`                                                     |
| `foldercode`        | The code of the folder, for example `/$BW_MAIL_BOX_RIGHTS$` for Exchange Online mailbox delegations |

`foldercode` is new in this version. It lets the script distinguish Exchange Online mailbox delegations, whose letters `A` to `H` would otherwise be confused with folder permissions. The comment of the default script in the wizard only lists the first three variables.

For security reasons, the script **MUST NOT** use Java classes (`java.`) or call `eval(`; such a script is ignored.

A right is the complete string of letters of one ACL, not a single permission: the script **SHOULD** therefore compare `folderrightaction` with the complete letter string of each permission level. The following example translates Exchange Online mailbox delegations, which contain one letter each, and the *Reviewer* and *Owner* folder permission levels:

```javascript
if (applicationfamily === "ExchangeOnline") {
  if (foldercode === "/$BW_MAIL_BOX_RIGHTS$") {
    switch (folderrightaction) {
      case "A":
        "Send As";
        break;
      case "B":
        "Send on Behalf";
        break;
      case "C":
        "Full Access";
        break;
    }
  } else {
    switch (folderrightaction) {
      case "IR":
        "Reviewer";
        break;
      case "IJKLMNOPQR":
        "Owner";
        break;
    }
  }
}
```


> [!warning] SharePoint Online rights combine the permissions of the permission levels (roles) defined in each tenant and site, and the letter string of a right depends on the permissions of its permission level and on the order in which they are collected. A mapping of SharePoint Online rights **MUST** be generated from the customer’s own `RolesDefinitions.csv` export: compute, for each permission level, the letter string of its permissions, add one `case` per string, and regenerate the mapping when permission levels change in the tenant.

The same constraint applies to the `SPO_direct_control_not_owner` control, which compares the rights of each direct ACL with the complete Full Control string `YVWXZ012UT45QKEFGBJCHAIMDSPON3RL`. If the Full Control level of the tenant produces a different string, adapt the filter of the view `O365_control_spo_fullaccess_not_owner`.  

### Pages

The Office 365 pages are standard detail and search pages. You can override them and add content to them with the usual mechanisms. For more details, see [Overriding detail pages](../identity-analytics/integration-guide/10-customization#overriding-detail-pages) and [Adding custom content in detail pages & dialog box](../identity-analytics/integration-guide/10-customization#adding-custom-content-in-detail-pages--dialog-box).
