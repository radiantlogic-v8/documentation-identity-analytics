---
title: "Identity Analytics Access Review Guide"
description: "Identity Analytics Access Review Guide"
---

# Introduction

This document describes the basic principles of self-service compliance driven Access Review in IA (Identity Analytics) as well as the best practices to configure and follow-up a review and manage the remediation processes.

This documentation will only focus on access review configuration, for a more general introduction to RadiantOne Identity Analytics and the configuration of the solution, please refer to the full documentation, available using the following URL:
https://developer.radiantlogic.com

> In IAP version 2.2 a new "sign off" principle has been added to the review process, as well as the the ability to launch the remediation process as soon as the reviewer signs off.
>
> In IAP version 3.0, the concept of review campaigns has been introduce with the ability to manage campaign configurations, including notification and scheduling capabilities. These new capabilities come with a new "Review Campaign Management" interface. The previous "Review Management" interface contains the finalized reviews in previous versions and has been renamed "Custom Review Management" interface.
>
> Due to these changes in behavior it is **necessary** to finalize **all** web-based reviews **before** upgrading IAP to version 3.0.

## General principles

### Access Review

Access review is often key when working within compliance restrictions (Sarbanes Oxley 404 for financial systems, CRBF 97-.02 in the world of banking, Solvency II in the insurance world, and ISAE 3402 for hosting companies, to name but a few). For this reason it is included in most security policies, including those based on the ISO standard number 27002.

#### What is an access review?

An access review shows whether a person's rights to access an application comply with a company's access management policy. It involves getting managers to check all the rights of their staff to access applications. It is an essential part of a company's information security and an effective access review will provide a list of all wrongly assigned rights. This list is then used to correct access rights and avoid failures in security. The result is no more risk of fraud, leaks of information, or problems linked to non-compliance.

An organisation's information system is constantly changing as are the people involved in it. Access reviews must be carried out regularly. Security standards set the minimum frequency at once per year, but in practice it needs to be carried out every three months to effectively tackle the risks of fraud and data leakage.

#### Who carries out access reviews?

The unit in charge of security is often responsible for preparing and organizing access reviews. However it is not responsible for the applications. Good practice assigns this responsibility to heads of departments and each department is responsible for its own applications. The sales and marketing managers are responsible for client management applications, the human resources managers are responsible for personnel management applications, and so on.

#### What are the different types of review?

The two main types of review are:

- The 'organisational review'
- The 'applications review'

There is one other type of review that is sometimes implemented when staff entry/exit procedures are complex, _i.e._ the HR data review.

##### The organisational review

These reviews involve asking a line manager to check that the people who work there have the correct application access rights.

Therefore, these reviews involve cross-checking HR information (on organisations and people) with applications information (people access rights on the different applications and their associated rights).

These are transverse reviews with regard to the applications (one person has access to several applications) and are limited to the access accounts of individuals.

##### The applications review

These reviews involve asking an application manager to check that access rights are correctly configured for their application.

This exercise is usually focused on a sub-set of access accounts:

1. Accounts with wider access rights
2. Technical accounts, known as 'service accounts' that are not linked to particular individuals.

It is not unusual for these two types of review to lead to additional sub-types of review, depending on the targets:

- Data access reviews (rights to access shared directories, Sharepoint, etc.)
- Distribution list reviews
- Website access reviews
- Orphaned account reviews (accounts for which an owner cannot be found)
- Dormant account reviews
- Privilege account reviews
- Etc.

#### How can you tell if an access right is valid?

There are two fundamental principles that enable the validation of access rights:

- The principle of the lowest rights: assigning only the rights that are strictly necessary to users. If a person has no particular need for a resource they should not have access to it.
- The principle of separation of tasks: those who originate a request should not be the same as those who carry it out and those who validate it. This is a first stage that helps avoid lots of errors and slip-ups later on.

In practice, without a formal security policy which defines the precise roles of all those involved, the legitimacy of access rights is left to managers to decide and who alone must assess the usefulness and the risks associated with the access rights assigned.

If a company has formalized the methods for assigning access rights, particularly via applications portals involving staged approval, the associated traces are a source of extra information that help to ensure the validity of the access rights assigned.

#### The major stages in an access review

Carrying out an access review involves several stages and several actors.

One of the first stages involves checking the data quality: can the data be used as it is or does it need to be reworked to make it usable?

Next, all available information must be gathered to compare one against the others. Such information is necessarily heterogenous, e.g. Windows, Unix, Mainframe, appliances, cloud applications, partners' applications, etc. In order to read and compare it, it must first be consolidated, _i.e._ formed into a single, structured source of data containing all the required information, _e.g._ all owners of access accounts arranged by the departments in which they work, etc.

The information must be rapidly comprehensible by those who have to read and validate it. This may involve improving the syntax of certain data, filtering (not displaying data that is not required for the decision making process), highlighting, etc.

The conduct of the review in itself involves asking numerous actors, heads of departments, and applications managers to validate the information. The organisation of this stage is crucial to the success of the review and often requires several awareness exercises, reminders, and so on.

Lastly, when all the above stages have been completed and errors have been identified, it must be possible to correct those errors. The correction process sometimes involves several tasks and several actors. It is only when this stage has been completed that the review is considered finalized.

#### Why is it difficult to carry out access reviews?

Obviously, an access review involves two major difficulties:

1. Getting an overall picture of people and their access rights.
2. Organizing and motivating a large number of actors.

##### Putting together an overall picture of people and of access rights to an information system.

This catalog of access rights provides the answers to the following questions:

- Who works for the organisation and where?
- What are their rights within applications and to what data do they have access?
- Which accesses have been used and by whom?
- Collating all this information often requires cross-checking dozens of different files. All too often this is done manually, which is very costly and results in poor quality catalogs.

Underestimating the importance of this stage will not only cause the associated costs to spiral, but also ensure that the data presented for validation will be at best partial, and at worst incorrect, and will in fact result in it being rejected by those in charge of validation.

##### Organizing a large number of actors to ask them to validate the correctness of the rights of access that have been assigned

It should be remembered here that most of these people will not be from the IT department and, therefore, they should be presented with relevant information, which will enable them to make decisions. All too often reviews merely present technical information, such as groups of accounts (Active Directory, etc.), whereas it would be much better to have the rights validated via these groups (rights to write in directories, access to distribution lists, etc.).

Their time is also limited and this operation is perceived as time-consuming. Therefore, all unnecessary stages should be avoided. For example, it is pointless to validate unchanged pieces of information, four times a year, or to have all access rights validated without considering the critical nature of some rights.

A lack of empathy between the actors often leads to rubber stamping signature of reviews. This gives a semblance of compliance, but when all is said and done, everyone has wasted their time.

As you will discover in the following chapter RadiantOne Identity Analytics solves this problem thanks to its self-service, compliance driven, access review capabilities.

### RadiantOne Identity Analytics Access Review Overview

RadiantOne Identity Analytics embeds compliance driven user access review interface. Through this interface you can configure an access review perimeter and run an access certification campaign. Users will then have to review their entries either online through the GUI or offline thanks to microsoft excel spreadsheet reports. At the end of the day, this interface also manages the remediation process so that you are sure that all decisions taken during the access certification campaign are enforced.

#### List of new Identity Analytics 3.0 features

Here is a quick list of the features available in compliance driven access review:

The User Access Review component has been completely redesigned in Identity Analytics 3.0 to offer the following new features:

- New "Review Campaign Management" interface for managing campaign configurations: create, modify, duplicate, delete, export/import configurations,
- Automated notifications and reminders, with the option of defining email templates and a notification strategy (scheduling),
- View reminder chronology in a timeline to update (add/delete) reminders,
- Definition of a campaign owner, who can start/stop/finalize/modify his/her own campaigns and view the review history.
- Access to the old "Review Management" interface renamed "Custom Review Management" to access reviews finalized in previous versions and web-based custom reviews,
- New six-step configuration wizard to define a review campaign:
  1. "Perimeter Selection" with the ability to define a static or dynamic tag-based review scope.
  2. "Review Strategy Selection" with the option to activate the AI AIDA Data Wizard in SaaS mode.
  3. "Preview Data" for a read-only check of the scope of the review campaign based on the current time slot.
  4. "Reviewer UI" for fine-tuning the reviewer interface (bulk action limit, comment templates, enable/disabe actions, etc.).
  5. "Campaign Schedule" to choose a frequency and manage notifications and reminders.
  6. "Campaign information" to define campaign name, description, tags, owners, etc.
- New ability to notify a selection of reviewers when a review has been started.
- An IDDM connector can now be configured in the remediation interfaces to take advantage of IDA to IDDM remediation once a review has been completed by a reviewer.

#### List of Other Identity Analytics features

All the features provided in previous versions are still available:

- Can configure a precise perimeter of what needs to be reviewed
- Can mix organisational review and application review in a single campaign
- Can run multiple campaigns at once
- Can automatically identify for each entry to review who is accountable for the review
- Can launch both a global/full access review or an incremental campaign focusing only on what changed since the last review
- Provides rich review end user interface including
  - risk scoring
  - identity context and permission context
  - review history information
  - filtering capabilities
  - reordering capabilities
  - bulk operations
  - self-service entries reassignment to peers (colleagues / other application owners) by enforcing RACI principles
  - exporting review data in excel format
  - running the review offline through excel spreadsheets
- Provides rich review management interface including
  - KPIs to follow up the campaign progress
    - review perimeter
    - Nb of applications to review
    - Nb of reviewers
    - Reviewed entries so far
    - Actions identities so far
    - Statistics around the nb of entries to review per reviewer (percentile, min, max, ...)
    - Completion ratio
    - Decision synthesis
    - Campaign activity
    - Backlog
    - ...
  - Real time view of the entries being reviewed with filtering/grouping/export capabilities and identity/permission context
  - Real time view of the actions identified so far with filtering/grouping/export capabilities and identity/permission context
  - Bulk review operations as an administrator
  - Reassigning review entries
  - Review campaign planning overview
  - Mail notification capabilities, including if needed entries to review as a dynamic attachment
  - Mail gentle-reminder capabilities, including if needed entries to review as a dynamic attachment
  - Generate, archive and provide digitally signed PDF compliance reports
- Provides both an embedded remediation workflow and ITSM connectivity to ServiceNow to delegate remediation activities to a third party ITSM
- Provides a "Sign-Off" feature to allow remediation even if all the reviewers have not finalized their review
- Provides rich remediation end user interface including
  - risk scoring
  - identity context and permission context
  - filtering capabilities
  - reordering capabilities
  - bulk operations
  - exporting remediation data in excel format
- Provides rich remediation management interface including
  - Tracking each requested remediation with a dedicated remediation process (new, in progress, done, won't fix)
  - KPIs to follow up the remediation progress
    - Total nb of remediation
    - Nb of active remediation
    - Nb of active remediation > 7 days
    - Nb of remediation done
    - Nb of remediation cancelled
    - Remediation velocity
    - Active remediation status
    - ...
  - Real time view of the entries being remediated with filtering/grouping/export capabilities and identity/permission context
  - Real time view of the discrepancies identified so far with filtering/grouping/export capabilities and identity/permission context
  - Bulk remediation operations as an administrator
  - Mail notification capabilities
- When leveraging ServiceNow for remediation, retrieve tickets numbers and track tickets status upon completion. Automatically spot discrepancies (action marked as done in ServiceNow and access still active in the target system...).

#### Behavior of a Review Campaign Running Over Several Timeslots

Identity Analytics supports two modes for handling user access review campaigns across multiple timeslots: **Standard Mode** and **Attached to Timeslot Mode**. These modes define how reviews handle changes in access data over time. The standard mode allows reviews to reflect updates and removals during the campaign, while the attached mode freezes the review scope to the exact state at campaign launch—ideal for audit and compliance requirements.

> Note that **Attached to Timeslot** mode is available in Identity Analytics from version 3.3 and higher.

##### Standard mode

In standard mode, the review campaign adapts to changes in data across timeslots. This means:The duration of a campaign can be spread over a time range comprising several data loads at different dates (timeslots).

Across multiple timeslots, some aspects of the review campaign remain constant, while others may vary.

- What remains the same timeslot after timeslot:
  - The reviewer. For example:
    - An identity changes line manager when the reviewer strategy relies on line managers.
    - An application right when the reviewer strategy relies on application managers
  - The reviewed access chain (i.e. the link Identity - Account - Permission - Application)
- What can change timeslot after timeslot:
  - Context information linked to the access chain (identity name/department/job, account expiry date, permission name, etc.). In this case, information from the current timeslot is displayed. Note that if you return to the timeslot on which the campaign was launched in the Portal, you will still see these modifications (i.e. those of the current timeslot), and not the information of the selected timeslot.
- If entries to be reviewed are deleted in the next timeslot (an account, an access, etc.), they will no longer appear in the IAP review page (if this has not been finalized, of course).
  - Note that deleted entries will be marked as "revoked" in the compliance report.
  - Also note that the content of the campaign follow-up page depends on the timeslot selected. This means that :
    - If entries are deleted in the next timeslot, the number of entries to be reviewed will change according to the timeslot selected in the portal in the list of entries to be reviewed (i.e., we'll have the initial list of entries to be reviewed on the timeslot on which the campaign was launched, and the "modified" list without the deleted entries on the next timeslot).
    - If context information (identity name/department/job, account expiry date, permission name, etc.) for certain entries is modified in the next timeslot, the information displayed will depend on the timeslot selected (i.e. initial information on the timeslot on which the campaign was launched, modified information on the current timeslot).

##### Attached to Timeslot Mode

Starting with Identity Analytics version 3.3, a new review mode titled "Attached to Timeslot" has been introduced. This mode allows user access reviews to be fixed to a specific timeslot, representing the access configurations at that particular time. Consequently, the review does not account for newer timeslots where some entries may have been removed since the review began. This mode is applicable to all review types: Application Access Rights Review, Account Repository Review, Group Membership Review, Safe Owner Review, and Server Review.

Using this mode is beneficial when strong compliance evidence is required, such as demonstrating to auditors that all accesses existing at a specific time have been reviewed. If the focus is more on reducing risks and enhancing operational efficiency rather than providing compliance proof, the standard mode, which considers access rights removal during the review campaign, might be more appropriate.

If your priority is minimizing risk and improving operational efficiency—rather than strict compliance—you can opt for the standard mode, which dynamically reflects access removals during the campaign, ensuring reviewers focus only on current, active access.

#### Role Assignment Prerequisites for UAR Management Access

The following personas can now access to the "Review Campaign Management" interface:

- The Identity Analytics administrator
- The Auditor
- The Campaign Owner (New IAP 3.0)

The _Identity Analytics administrator_ is either a **functional administrator** ('functionaladmin' role) or a **technical administrator** ('technicaladmin' role) of the RadiantOne Identity Analytics platform. She/he can create, modify, duplicate, delete, export/import review campaign configurations. From a selected review campaign he can also launch, pause/resume, finalize, follow-up, download the compliance report, and delete a review instance.

The _Identity Analytics auditor_ is **auditor** ('auditor' role) of the RadiantOne Identity Analytics platform. She/He has access in readonly to all the interfaces, can check the history of review instances and can download the compliance reports.

The _campaign owner_ is defined by the administrator when creating a new review campaign. She/he can be any identity with a valid email address. Once defined as owner of a campaign, she/he has access to the campaign and can edit the review campaign configuration, launch and manage review instances. The Campaign Owner does not need to have a specific role.

Of course, the Identity Analytics administrator must ensure that all these personas have a valid e-mail address associated with their identity in Identity Analytics to receive notifications.

#### Behavior of the Scheduling

The scheduling is done through a workflow that needs to be up and running: the scheduler. To check the status or start the workflow, using the left menu bar, go to "Settings" > "System" and then click on the "Scheduler" button:

![](./media/IAP257.png)

Specify the hour you need to start the scheduler, click on "Start Scheduler" and then confirm:

![](./media/IAP256.png)

When the scheduler is started, you'll find in the same page the information about the lifecycle of the scheduler:

![](./media/IAP258.png)

When a campaign reaches its start date, the revision instance will be launched on the specified start date, at the same time as the scheduler's start time.

> **Notes:**
>
> 1. When the scheduler is restarted, it will launch all overdue review instances. Please make sure you've deactivated any campaigns you don't want to launch before starting the scheduler, otherwise these campaigns will be launched and notifications sent to all reviewers if you have them activated.
> 2. If the current review instance is still active on the start date of the next schedule, the new review instance will not be launched until the initial one is finalized. In that case, the next start date of the campaign is set to "Behind Schedule". Once the current review instance has been finalized, the next start date is one day after the finalization date.

#### Purging Behavior

When an "attached to timeslot" review campaign is active and linked to a specific timeslot, that timeslot cannot be purged. Purging will only be allowed once all reviews associated with the timeslot have been finalized or deleted.

If the tickets purge is enabled in the technical configuration ('Disable tickets purge' unchecked), finalized review instances older than the keep period are purged with their timeslot: their history, details page and compliance report are no longer available from the portal. Download the compliance reports you need to keep before the purge.
