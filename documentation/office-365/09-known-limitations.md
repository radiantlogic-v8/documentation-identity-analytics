---
title: "Office 365 - Known limitations"
description: "Office 365 - Known limitations"
---

# Known limitations

This page lists the known limitations of the Office 365 module.

## Pages and ACLs

- When Office 365 is activated, SharePoint Online site collections, Exchange Online mailboxes and OneDrive drives aren’t listed on the **Share** search page, and SharePoint Online, Exchange Online and OneDrive folders aren’t listed on the **Folder** search page. Use the Office 365 search pages instead.
- OneDrive rights are displayed with the standard Windows columns, because OneDrive rights are collected with the same letters as Windows file system rights.
- SharePoint Online permission levels can be customised in each tenant. The SharePoint Online columns group the SharePoint permissions according to Microsoft’s default permission levels, so a custom permission level can tick a column that its name doesn’t suggest (for example a custom “Read” level that also includes **Manage Lists** ticks **Modify**). Open the **SharePoint Online ACL details** window to see the exact permissions.
- In the **ACLs at a group level** section of SharePoint Online sites and content, the rights columns are wide enough to push the **Name**, **Group Code** and **Repository Name** columns out of view. Select an ACL to display the horizontal scrollbar, or read the group in the **Selected ACL group details** section.  
- SharePoint Online and Exchange Online folders opened from the generic **Folder** details page are displayed with the Windows columns. Open them from the Office 365 search pages to see the columns of their workload.
- In the **Delegations** tab of the **Mailbox detail** window, the **Mailbox type** column shows the raw value (for example `SharedMailbox`).
- In the **OneDrive** tab and the **OneDrive tree**, the **Permission details** of the root of a drive show the type **Share**, while the tree shows **Root**.

## Integration

The limitations visible to end users are listed in the [Pages and ACLs](#pages-and-acls) section (Office 365 pages) and in [Office 365 ACLs](./05-acl-and-rights/#office-365-acls) (SharePoint Online permission levels, **Special rights** column). The following limitations concern the configuration and the loaded data:

- **Non‑NTFS rights.** The SharePoint Online and Exchange Online grids read the collected `action` attribute directly. Any other application family loaded with rights that don’t follow the Windows letters falls back to the standard Windows display, which is then incorrect, and its counters are computed as for Windows shares.
- **Generic Folder details page.** SharePoint Online and Exchange Online folders opened from the generic **Folder** details page are displayed with the Windows columns, because this page doesn’t pass the share family to the ACL fragment.  
- **Dashboards.** The five dashboards don’t depend on `isOffice365Active`: once they are shared, they are listed in the **Office 365 reports** menu even when `isOffice365Active` is `false`.
