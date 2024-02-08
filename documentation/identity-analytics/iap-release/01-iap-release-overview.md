---
title: "Identity Analytics Release Notes"
description : "Identity Analytics Release Notes"
---

# Identity Analytics Release Notes  

## IAP/IGRC Compatibility matrix

IAP leverages improvements applied to the IGRC product. Please refer to the following table for more information :

|              | IAP 1.0 -- 1.2 | IAP 1.3 -- 1.7 | IAP 1.8 | IAP 2.0 - 2.2 |
| :----------- | :------------: | :------------: | :-----: | :-----------: |
| Curie R1     |     **X**      |       -        |    -    |       -       |
| Curie R2     |       -        |     **X**      |    -    |       -       |
| Curie R2 SP1 |       -        |     **X**      |    -    |       -       |
| Curie R3     |       -        |     **X**      |    -    |       -       |
| Curie R3 SP4 |       -        |       -        |  **X**  |       -       |
| Descartes R1 |       -        |       -        |  **X**  |       -       |
| Descartes R2 |       -        |       -        |  **X**  |     **X**     |

## IAP release content

For a full list of changes to IAP please refer the to following release notes:

- [IAP 2.x release notes](02-iap-2-release-notes.md "IAP release notes" )
- [IAP 1.x release notes](03-iap-1-release-notes.md "IAP release notes" )

### Version 2.2

Update of the "web based" user access review with the extension to all reviews of explicit validation by the reviewer ("sign-off")and automatic update of remediation status:</p>

- Safe Permissions Review,
- Repository Accounts Review,
- Groups Direct Membership Review.

### Version 2.1

Improvement of the "web based" user access review:

- Add of a new group membership review,
- For the Application Rights Review only, addition of explicit validation by the reviewer with the "sign-off" action,
- Once entries have been signed off by the reviewer, they can be switched to "Remediation Pending" status automatically or manually (action "proceed now" by the review campaign owner), even if the review campaign has not been finalized,
- The automatic status change is carried out by a batch run daily, and is configured in the technical configuration (activation and delay in days).

New group glossary management dashboard available from repository analytics reports to mass update group description and group sensitivity level.

Ability to hide Role Mining and PAM Booster dashboards and menuitems if there are not required by updating the technical configuration of the project.

Improvement of the risk ranking.

### Version 2.0

All User Access Review reviewer interfaces have been re-designed to provide a smoother and more efficient experience to the reviewers:  

- Responsive design of the interface
- New and enhanced filtering capabilities
- A progress bar is now displayed at the top of the tables
- A new option to freeze columns  
- Unified display of pending or in progress web-based (IAP) and custom (workflow) reviews in Access360
- Offline mode added to Access360 to make reviewers autonomous  

Enhanced user experience for review owners:  

- Owner escalation management of review campaigns
- New "Reviewer" resource owner type in addition to "Business Owner" and "Technical Owner" to facilitate reviewer identification

PAM Booster is now embedded by default in IAP including the CyberArk Safes User Access Review.  

Consideration of new license levels Observability, Governance, Compliance.  

Multiple bugfixes (see release note).  

### Version 1.8

RoleMining module is now embedded by default in IAP.  
This version includes multiple bugfixes, please see the release notes above for the full list.  

### Version 1.7

Version 1.7 includes among others:  
  
- A new module, the Control browser, that provides access to all the control results and to launch ad-hoc remediation.  
- New technical administrator home page with KPIs and shortcuts  
- New Modern look and feel  
- New mashup dashboards for admins and resource owners  
- New access review compliance dashboards at an application level and at a repository level  
- Perimeter based search pages are now accessible to resource owners  
- New controls:
  - Permissions without description
  - Folders without description
  - High sensitivity group with new accounts
  - Extreme sensitive group with new accounts
  - Several accounts with the same identity at a repository level
  - Several accounts with the same identity at an application level
  - Inactive account and owner left the company 2 years ago
  - AD/Azure account created more than 7 days after identity arrival
  - Identity manages themselves
  - Contractor leaves within 30 days
  - Identities with the same name
  - Identities with the same mail
  - Identity with multiple accounts within a repository
  - Identity with multiple accounts within an application
- Improve reconciliation management with bulk operations  
- Delegation is now available as a Tab in access360  
- Auditor role can now connect and access the access review manager and the remediation manager in read-only mode  
- Controls scope attribute is now filled with the control target (account, right, ...)  
- Hyperlinks in KPIs in access review management and remediation management  

### Version 1.6

#### Pre-requisits

IAP 1.6 includes by default project dashboards, a feature added in version Curie R3 of the product (see [here](https://documentation.brainwavegrc.com/Descartes/docs/igrc-platform/dashboards/advanced-configuration/project-based-dashboards/) for more information). IAP 1.6 is as such compatible with Curie R2, however, all project dashboards will be ignored.  

When upgrading to IAP 1.6 in a version Curie R2 of the product and when the default dashboards are used in the project, please do not remove them from the project when migrating.  

In some cases it can be necessary to navigate to the dashboard management page and "clean up" the existing dashboards to avoid duplicates.  

#### Content

Access review improvements:  

- Add a campaign initialization status
- Can pause/resume a campaign
- Reviewer can ask for a change (ok, revoke, update)
- Reviewer can mark entries as “I am not the reviewer”
- Reviewer can now see delegated (RACI) entries
- Default comments provided for the reviewer
- Self-review campaign

Remediation improvements:  

- Discrepancies computed for account based reviews
- Jira Cloud
- Universal ITSM
- RPA

User empowerment:  

- New Mashup Dashboards

### IAS 1.5

IAS Remediation:  

- Improved remediation process
- ServiceNow support

### IAS 1.4

IAS Review process:  

- Accounts review
- Access rights reviewSOD
- Improved SOD analysisMining
- New search analytics mining reportsReports Subscription
- Officially availableMashup Dashboard
- Project based mashups (starting with upcoming R3 release)