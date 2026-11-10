---
title: "Office 365 - Introduction"
description: "Office 365 - Introduction"
---

# Office 365

## Introduction

Identity Analytics provides dedicated pages, controls, metadata and dashboards for the Microsoft 365 workloads loaded as unstructured data: SharePoint Online, Exchange Online and OneDrive. It provides:

- seven search pages, each with its detail page: SharePoint Online site collections, content and groups, OneDrive drives and files, Exchange Online mailboxes and mailbox folders;
- ACL grids and ACL detail windows adapted to SharePoint Online and Exchange Online rights, and a **Delegations** sub‑tab on Exchange Online mailboxes;
- an **Office 365** sub‑tab on the identity details page and a **My Office 365** tab in Access 360;
- 22 controls and five dashboards, grouped in the **Office 365 reports** menu, that report their results;
- four metadata that compute read, write, full control, view and delegation counts for SharePoint Online and Exchange Online.

The Office 365 module is optional. It is deactivated by default (the configuration variable `isOffice365Active` is `false`) and only concerns the projects that load SharePoint Online, Exchange Online or OneDrive data.

The generic **Share** and **Folder** pages were designed for Windows file servers. The Office 365 pages show the same kind of information in the vocabulary of each workload: SharePoint Online ACLs show a **Permission Visibility** column, Exchange Online ACLs show a **View** column, mailbox delegations (**Send As**, **Full Access**, …) are listed on the mailbox itself, and dedicated controls and dashboards report broken inheritance, guest access, public access and risky delegations. Use these pages to answer questions such as “Who can read this SharePoint site?”, “Who can send emails as this shared mailbox?” or “Which OneDrive drives are shared with everyone?”.

The Office 365 pages are available only if the end user has the appropriate license (Booster for Data Governance / Unstructured Data) and if Office 365 has been activated in the project. For more details on the activation, see [Activation](./02-prerequisites-and-activation#activation).

By default, only users with the `functionaladmin` or `technicaladmin` roles can access the Office 365 search pages. The **Office 365** sub‑tab of the identity details page and the **My Office 365** tab of Access 360 are described in [Office 365 tab](./04-office-365-tab#office-365-tab).

The five Office 365 dashboards are delivered in the project but aren’t shared by default, so they don’t appear in the menu after installation. To make them available, either modify them in the project so that they are shared by default, or duplicate them from the **Manage dashboards** page (see [Top of pages options](../identity-analytics/enduser-guide/01-introduction#top-of-pages-options)) and share the copies with the users who need them. For more details, see [Publication](./07-dashboards-and-reports#publication).  

In all tables of the Office 365 pages, as in any table in IAS/IAP, the end user can configure and add columns and KPIs by right‑clicking the table and selecting **Configure**. For more information, see [How to configure tables, columns and export data](../identity-analytics/enduser-guide/07-customization#standard-tables).

## Structure of the module

The Office 365 module is described in the following pages:

- [Prerequisites and activation](./02-prerequisites-and-activation): license, data loading, activation of the module, roles and features.
- [Search and detail pages](./03-search-and-detail-pages/): the seven search pages and their detail pages. One page per family, structured in the same way:
  - [SharePoint Online pages](./03-search-and-detail-pages/01-sharepoint-online)
  - [OneDrive pages](./03-search-and-detail-pages/02-onedrive)
  - [Exchange Online pages](./03-search-and-detail-pages/03-exchange-online)
- [Office 365 tab](./04-office-365-tab): the tab of the identity details page and of Access 360, and the Office 365 data shown in the generic pages.
- [ACLs and rights](./05-acl-and-rights/): display of the SharePoint Online, Exchange Online and OneDrive rights, mapping of the rights to columns and counters. One page per workload, structured in the same way:
  - [SharePoint Online ACLs](./05-acl-and-rights/01-sharepoint-online)
  - [Exchange Online ACLs](./05-acl-and-rights/02-exchange-online)
  - [OneDrive ACLs](./05-acl-and-rights/03-onedrive)
- [Controls](./06-controls): the Office 365 controls, their parameters and the Controls Browser.
- [Dashboards and reports](./07-dashboards-and-reports): the **Office 365 reports** menu, its dashboards, their publication and the analytics reports.
- [Metadata and customization](./08-metadata-and-customization): the Office 365 metadata, custom folder right mapping and page customization.
- [Known limitations](./09-known-limitations).
