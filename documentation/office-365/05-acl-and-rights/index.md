---
title: "Office 365 - ACLs and rights"
description: "Office 365 - ACLs and rights"
---

# ACLs and rights

This page describes how the SharePoint Online, Exchange Online and OneDrive rights are displayed, and how they are mapped to the ACL columns and counters. The rights of each workload are described in a dedicated page.

## Office 365 ACLs

SharePoint Online and Exchange Online don’t use Windows file system rights. Each SharePoint Online or Exchange Online ACL is collected as a list of permission letters, one letter per permission (for example `YVWXZ…` for a SharePoint Online ACL). To keep the display readable, Identity Analytics groups these permissions into a few columns, using the vocabulary of each workload. On share and folder detail pages, in the **ACLs at a group level** and **ACLs at an account level** sections, the basic ACL columns therefore depend on the share family:

| **Share family**  | **Basic ACL columns**                                                                              | **Show Advanced Permissions** |
| :---------------- | :------------------------------------------------------------------------------------------------- | :---------------------------- |
| SharePointOnline  | Full Control, Modify, Permission Visibility, Read, Write, Special rights                           | Not available                 |
| ExchangeOnline    | Full Control, Modify, View, Read, Write, Special rights                                            | Not available                 |
| Any other family  | Full Control, Modify, Read & Execute, Read, Write, Special rights (see [Basic ACLs](/identity-analytics/enduser-guide/06-acl#basic-acls))  | Available                     |

The **Sharing list** of the **Office 365** tab uses the same columns, without **Special rights**, followed by the **ACL source** column (see [Office 365 tab](/office-365/04-office-365-tab#office-365-tab)). For OneDrive, the Sharing list uses the Windows columns (**Full Control**, **Modify**, **Read & Execute**, **Read**, **Write**).

For SharePoint Online and Exchange Online, a column is ticked when the ACL contains **at least one** of the permissions listed for that column below, whatever their order. The columns are groupings made by Identity Analytics to simplify the display; they aren’t SharePoint Online or Exchange Online permission levels. For example, **Full Control** is ticked by any of three SharePoint Online administration permissions. Because Microsoft permission levels are cumulative, an ACL that ticks a higher column usually ticks the lower ones too (for example, an ACL granted through the SharePoint Online *Full Control* permission level also ticks **Modify**, **Permission Visibility**, **Read** and **Write**). A permission that isn’t listed for any column doesn’t tick any column, and an ACL made only of such permissions ticks no column; these permissions are visible in the ACL details window.

Selecting an ACL and clicking the magnifier icon on the right side of the table opens a window listing every permission granted by the ACL, with its code and meaning. For SharePoint Online and Exchange Online, the magnifier icon is disabled until an ACL is selected.

> **Note** For SharePoint Online and Exchange Online, the **Special rights** column is computed with the Windows rule described in [Basic ACLs](/identity-analytics/enduser-guide/06-acl#basic-acls): the permission letters are read as if they were Windows rights letters. It therefore doesn’t correspond to a SharePoint Online or Exchange Online permission (for example, an Exchange Online ACL that only contains **Folder Visible** ticks **Special rights**). Use the ACL details window to see the exact permissions.  

The read, write, full control and view counters displayed on the Office 365 search and detail pages (for example **Nb. of Read Access** or **Number of Write Access**) use the same permission letters as the columns, and count the active accounts that hold at least one of them. They differ from the ACL columns in the following ways:

- An ACL column describes one ACL, granted to a group or to an account. A counter counts distinct active accounts, including those that get the right through a group.
- On a site collection or a mailbox, a counter takes into account all the elements of the site or all the folders of the mailbox. On a list, folder or mailbox folder, it only takes into account the rights on that element.
- There is no counter for the **Modify** and **Permission Visibility** columns.
- OneDrive counters are computed as for Windows shares and folders.

## Pages by workload

The rights of each workload are described in a dedicated page. The three pages are structured in the same way, so that the same information is found in the same place:

- [SharePoint Online ACLs](/office-365/05-acl-and-rights/01-sharepoint-online): rights of SharePoint Online sites, lists and folders.
- [Exchange Online ACLs](/office-365/05-acl-and-rights/02-exchange-online): rights of Exchange Online mailbox folders, and mailbox delegations.
- [OneDrive ACLs](/office-365/05-acl-and-rights/03-onedrive): rights of OneDrive drives, files and folders.

Each page has the following sections:

| **Section**                  | **Content**                                                                                          |
| :--------------------------- | :--------------------------------------------------------------------------------------------------- |
| Overview                     | How the rights of the workload are collected and displayed                                          |
| ACL columns                  | The columns of the ACL grids and the permissions that tick them                                     |
| Permission codes             | The meaning of each permission code                                                                  |
| ACL details window           | The window that lists the permissions of an ACL                                                      |
| Counters                     | The access counters and the letters they count                                                       |
| Sharing list and delegations | The Sharing list of the Office 365 tab and, for Exchange Online, the mailbox delegations             |
| Integration                  | Fragments, templates, regular expressions, dialogs and metadata, for customisation                   |
| Known limitations            | The limitations of the workload                                                                      |

## Office 365 rights in unstructured data reviews

In an unstructured data review, the rights are displayed to the reviewers as they are collected (for example `YVWXZ012UT45…` for a SharePoint Online ACL), unless the review campaign defines a custom folder right mapping that translates them into readable labels. For more details, see [Unstructured data reviews: custom folder right mapping](/office-365/08-metadata-and-customization#unstructured-data-reviews-custom-folder-right-mapping).

## Other share families

Basic ACLs are computed from the rights collected for each ACL, assuming that they follow the Windows (NTFS) rights letters. If an application family other than SharePointOnline and ExchangeOnline is loaded with rights that don’t follow the Windows letters, its ACLs are displayed with the standard Windows columns, and these columns are incorrect. For more details, see [Known limitations](/office-365/09-known-limitations).

## Rights mapping

SharePoint Online and Exchange Online rights are collected as strings of permission letters in the `action` attribute of each ACL. Before the Office 365 pages, share and folder pages only supported Windows (NTFS) rights, through the `basic` ACL attribute that the product computes from `action`. With SharePoint Online or Exchange Online letters, `basic` and every display built on it are meaningless. The Office 365 ACL grids, ACL details windows and metadata therefore read `action` directly and group its letters into a few readable columns and counters. The resulting tables are given in the page of each workload (see [Pages by workload](#pages-by-workload)); this section describes where they are defined, for customisation and for your own views and rules.

### ACL grids

The **ACLs at a group level** and **ACLs at an account level** grids are defined in the fragment `fragmentSharedfolderAcls` (`/webportal/pages/bw_fragments/sharedfolder/acls.page`). The fragment receives the share family in its `inappfamily` parameter and selects the columns: `SharePointOnline`, `ExchangeOnline`, or the Windows columns for any other value (including OneDrive). The **Show Advanced Permissions** checkbox is hidden for `SharePointOnline` and `ExchangeOnline`.

The **Special rights** column of all grids uses the Windows service `bwf_jsHasSpecialPermission` (`/webportal/pages/bw_fragments/sharedfolder/resources.javascript`), which reads the letters as Windows rights (`OPGDSMLAWFERX`) and ticks the column when they don’t form an exact combination of Windows basic permissions. For SharePoint Online and Exchange Online, this column has no specific meaning.

### ACL details windows

The magnifier icon of the grids opens `bwf_sharepointonlineAclBreakdownDialog`, `bwf_exchangeonlineAclBreakdownDialog` or, in the Sharing list, `bwf_onedriveAclBreakdownDialog` (`/webportal/pages/bw_office365/resources/dialogs.page`). Each window splits the `action` of the selected ACL into single letters and translates each letter with a mapping of `/webportal/pages/bw_office365/resources/mappings.page`. The SharePoint Online and Exchange Online labels and meanings are the NLS entries `bwf_advancedactions_NLS.sharepointonline.*` and `bwf_advancedactions_NLS.exchangeonline.*` (`/webportal/pages/bw_fragments/sharedfolder/resources.page`); the OneDrive labels are the Windows rights labels (`bwf_sharedfolder_helpNLS`).

### Counters

The read, write, full control and view counters are computed by the metadata described in [Metadata](/office-365/08-metadata-and-customization#metadata). Each metadata uses a business view (`O365_analytics_nbaccess_bv` for sites and mailboxes, `O365_folders_nbaccess_bv` for lists and folders) that counts the distinct active accounts whose rights (`action`) contain at least one of the following letters (case‑insensitive `ilike` filters):

| **Counter**                  | **SharePoint Online**       | **Exchange Online**          |
| :--------------------------- | :-------------------------- | :--------------------------- |
| `nbreadaccess`               | `Y`, `K`, `4`, `0`, `1`     | `I`                          |
| `nbwriteaccess`              | `V`, `W`, `X`, `Z`          | `J`, `K`, `L`, `M`, `N`      |
| `nbfullcontrolaccess`        | `A`, `C`, `D`               | `P`                          |
| `nbviewaccess`               | -                           | `R`                          |

These are the same letters as the corresponding ACL columns. How the counters differ from the ACL columns (they count accounts after group membership is resolved, the site and mailbox counters cover all the elements of the site or mailbox, and there is no counter for **Modify** and **Permission Visibility**) is described in [Office 365 ACLs](#office-365-acls).
