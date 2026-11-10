---
title: "Office 365 - Prerequisites and activation"
description: "Office 365 - Prerequisites and activation"
---

# Prerequisites and activation

This page lists what the Office 365 module needs and how to activate it.

## Prerequisites

### License

The Office 365 search and detail pages require the **Booster for Data Governance / Unstructured Data** license (feature `unstructureddata_license`).

### Data loading

The data of the three sources (SharePoint Online, Exchange Online and OneDrive) **MUST** be loaded through the `bw_office_365` collection facet, available on the Radiant Logic marketplace.

The Office 365 pages, controls and metadata rely on the following conventions of the data loaded by this facet. Data loaded differently **MUST** follow them:

- Each SharePoint Online site collection, Exchange Online mailbox and OneDrive drive is loaded as an application of type `Filesystem` with the application family `SharePointOnline`, `ExchangeOnline` or `OneDrive`. The Exchange Online controls only consider applications of type `Filesystem`.
- The permission type identifies the element:
  - SharePoint Online: `SiteCollections` (root of a site, code `/`), `List` and `Folder`;
  - OneDrive: `R` (root of a drive), `D` (folder) and `F` (file);
  - Exchange Online: `MailboxFolder` for the mailbox folders, the root of a mailbox having the code `/` and the name *Top of Information Store*, and `UserMailbox` or `SharedMailbox` for the entry that holds the mailbox delegations.
- Exchange Online mailbox delegations are loaded as rights on the pseudo-folder `/$BW_MAIL_BOX_RIGHTS$` of the mailbox.
- The `action` attribute of each ACL **MUST** contain the rights letters of the workload, one letter per permission: SharePoint Online permission letters (`A` to `Z`, `0` to `5`), Exchange Online delegation letters (`A` to `H`, on `/$BW_MAIL_BOX_RIGHTS$`) and folder letters (`I` to `T`), or Windows rights letters for OneDrive. For the meaning of each letter, see [Office 365 ACLs](./05-acl-and-rights/#office-365-acls).
- The group with the code `EVERYONE_AAD` is considered as the public group (everyone in the tenant).
- Guest accounts are Microsoft Entra ID accounts with the value `Guest` in the `custom1` attribute.
- The owner of a site, mailbox or drive is loaded as the business owner or technical owner of the application. Resources without one are reported by the “without owner” controls.

## Activation

The Office 365 features are activated by the configuration variable `isOffice365Active`, declared in the configuration `office365` (`/configurations/bw_office365/office365.configvariables`):

| **Variable**        | **Type** | **Display name**     | **Default value** |
| :------------------ | :------- | :------------------- | :---------------- |
| `isOffice365Active` | Boolean  | Is Office 365 active | `false`           |

When `isOffice365Active` is `true`:

- the seven Office 365 entries are displayed in the **Search** menu;
- the Office 365 controls and the `spo_sitemetrics`, `spo_foldermetrics`, `eol_mailboxmetrics` and `eol_foldermetrics` metadata are computed by the execution plan;
- the **Office 365** sub‑tab is displayed on the identity details page;
- the **My Office 365** tab is displayed in Access 360 for the users who have the `enduser360_office365tab` feature;
- SharePoint Online sites, Exchange Online mailboxes and OneDrive drives are no longer listed on the **Share** search page, and SharePoint Online, Exchange Online and OneDrive folders are no longer listed on the **Folder** search page: they are searched with the Office 365 search pages instead.


The following items don’t depend on `isOffice365Active`:

- the Office 365 search and detail pages themselves, which are protected by features only;
- the five dashboards of the **Office 365 reports** menu, which are delivered without being shared (see [Dashboards](./07-dashboards-and-reports#dashboards));
- the SharePoint Online and Exchange Online ACL grids on share and folder detail pages.

The **Delegations** sub‑tab of Exchange Online mailboxes is displayed only when the `eol_mailboxmetrics` metadata has found at least one delegation, so it is hidden as long as the metadata hasn’t been computed.

## Roles and features

The Office 365 features are grouped in the following feature sets:

| **Feature set**         | **Description**                                           | **Granted by default to**                       |
| :---------------------- | :-------------------------------------------------------- | :---------------------------------------------- |
| `o365_searchpages`      | Office 365 search pages and their menu entries            | `functionaladmin`, `technicaladmin`             |
| `browsing_o365_reports` | Office 365 browsing reports and dashboard control lists   | `user`, `functionaladmin`, `technicaladmin`     |
| `o365_actions`          | Actions on Office 365 objects                             | `functionaladmin`, `technicaladmin`             |
| `o365_designer`         | Access to specific Office 365 views                       | `functionaladmin`, `technicaladmin`, `designer` |
| `o365_technicaladmin`   | Reserved                                                  | `functionaladmin`, `technicaladmin`             |

The features of the `o365_actions` and `o365_technicaladmin` feature sets aren’t used by the current pages.

Each search page has its own feature, so that you can grant access to one workload only:

| **Feature**                                  | **Search page**              |
| :------------------------------------------- | :--------------------------- |
| `office365_searchpages_spositecollections`   | SharePointOnline - Site      |
| `office365_searchpages_spocontent`           | SharePointOnline - Content   |
| `office365_searchpages_spogroup`             | SharePointOnline - Group     |
| `office365_searchpages_onedriveshare`        | OneDrive - Share             |
| `office365_searchpages_onedrivefolder`       | OneDrive - Content           |
| `office365_searchpages_eolmailboxes`         | ExchangeOnline - Mailbox     |
| `office365_searchpages_eolmailboxfolders`    | ExchangeOnline - Folder      |

The Office 365 search pages reuse the features of the standard share, folder and group search pages for the rule editor, tags and analytics (for example `sharesearch_rulemode`, `sharedfoldersearch_updatetags` or `groupsearch_analytics`).

The five dashboards are delivered with the publication rule `$technicaladmin`, but they aren’t shared by default (see [Dashboards](./07-dashboards-and-reports#dashboards)). The **Control identifier** combobox of each control dashboard is filled by a published view protected by a feature of the `browsing_o365_reports` feature set: `office365_reports_eo` (Exchange Online), `office365_reports_spo` (SharePoint Online site and content) and `office365_reports_onedrive` (OneDrive). A user who can open a dashboard without the corresponding feature gets an empty list.

The **My Office 365** tab of Access 360 requires the `enduser360_office365tab` feature (“Shows the Office365 tab for end users”), which belongs to the `enduser360` feature set.

