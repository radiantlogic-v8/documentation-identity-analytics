---
title: "Identity Analytics Integration Guide"
description : "Identity Analytics Integration Guide"
---

# Available Analytics

A lot of analytics are available of the shelf, for an updated list of the available analytics, you **SHOULD** consult "Configuration &rarr; System &rarr; Available analytics".

![](./media/image57.png)

Here is an extract for your information:

---

- **Type:** account
- **Page:** `access360r_accountgroups360`
- **Name:** 360° view of the account groups
- **Description:** This report presents all groups in the account in the form of a network graph. The direction of the arrow means 'is in'. It is possible to restrict the display to direct groups only. It is possible to display the details of the groups.

---

- **Type:** account
- **Page:** `access360r_accountpermissions360`
- **Name:** 360° view of the account permissions
- **Description:** This report presents all account permissions in the form of a network graph. The direction of the arrow means 'contains'. It is possible to restrict the display to direct permissions only. It is possible to display the details of the permissions.

---

- **Type:** account
- **Page:** `accounttimeline`
- **Name:** Account timeline
- **Description:** This report presents the evolutions that have occurred over time. The timeline presents the different timeslots as well as the major events that occurred at each loading. It is possible to select a date to display the details of the identified changes. It is also possible to select a time range by pressing the Ctrl key and clicking on two dates in the timeline.

---

- **Type:** application
- **Page:** `access360r_application_accessrights360cs`
- **Name:** access analysis
- **Description:** This report presnts the access rights of the application in a pivot table. Only the 'application profile' type rights directly associated with active accounts are taken into account. it is possible to identify only the changes made since a given date. The columns displayed are configurable and the results can be exported, right click on the table to do so.

---

- **Type:** application
- **Page:** `access360r_application_analytics`
- **Name:** self-service analytics
- **Description:** This report presents the access rights of the application in the form of a dynamic pivot table where it is possible to select the analysis dimensions. Only the 'application profile' type rights directly associated with the active accounts are taken into account. it is possible to identify only the changes made since a given date. the columns displayed are configurable and the results can be exported, right-click on the table to do so.

---

- **Type:** application
- **Page:** `access360r_application_similarprofile`
- **Name:** Similar profiles analytics
- **Description:** This report allows you to analyze the similarities between application profiles. A calculation is performed to identify the number of active accounts in common between the profiles. The results are presented in the form of a pivot table. It is also possible to present the results in a list format in order to facilitate the export of results. Regardless of the display mode selected, it is possible to obtain details on the 'application profiles' as well as to identify the common accounts and the specific accounts of each profile.

---

- **Type:** application
- **Page:** `access360r_application_permissionmap`
- **Name:** Permissions map
- **Description:** This report presents the permissions accessible by the application accounts in the form of a card. The size of the blocks can either be proportional to the number of accounts, inversely proportional to the number of accounts or identical. Only active accounts are taken into account. Only the rights directly associated with the accounts are taken into account. Only permissions of type 'application profile' are taken into account. It is possible to restrict the display to direct members or to display all members. It is possible to display the details of the permissions by clicking on the blocks.

---

- **Type:** application
- **Page:** `applicationtimeline`
- **Name:** Application timeline
- **Description:** This report presents the evolutions that have occurred over time. The timeline presents the different timeslots as well as the major events that occurred at each loading. It is possible to select a date to display the details of the identified changes. It is also possible to select a time range by pressing the Ctrl key and clicking on two dates in the timeline.

---

- **Type:** application
- **Page:** `access360r_application_filesources`
- **Name:** Files used to fulfill the ledger
- **Description:** This report lists the source files used to consolidate information about this application. Note that it is possible for internal technical configuration reasons that only some of the files used are listed here. In case of doubt, we invite you to contact the platform administrator who has the complete list and will be able to give you more information.

---

- **Type:** application
- **Page:** `access360r_application_accessrights360`
- **Name:** access rights list
- **Description:** This report lists the access rights of the application. Only the 'application profile' type rights directly associated with active accounts are taken into account. it is possible to identify only the changes made since a given date. The columns displayed are configurable and the results can be exported, right click on the table to do so.

---

- **Type:** group
- **Page:** `access360r_groupsubgroups360`
- **Name:** 360° view of the sub-groups
- **Description:** This report presents the sub-groups of the group in the form of a network graph. The direction of the arrow means 'contains'. It is possible to display the details of the groups.

---

- **Type:** group
- **Page:** `access360r_group_analytics`
- **Name:** self-service analytics
- **Description:** This report presents the active accounts of the group in the form of a dynamic pivot table where it is possible to select the analysis dimensions. You can select either direct accounts or all accounts. it is possible to identify only the changes made since a given date. the columns displayed are configurable and the results can be exported, right-click on the table to do so.

---

- **Type:** group
- **Page:** `grouptimeline`
- **Name:** Group timeline
- **Description:** This report presents the evolutions that have occurred over time. The timeline presents the different timeslots as well as the major events that occurred at each loading. It is possible to select a date to display the details of the identified changes. It is also possible to select a time range by pressing the Ctrl key and clicking on two dates in the timeline.

---

- **Type:** identity
- **Page:** `organisationgroupscs360detail`
- **Name:** Managed organisations AD groups analysis
- **Description:** This report lists the Active Directory groups of the members of the managed organisations in a form of a pivot table. Only active accounts are taken into account. Only the groups directly associated with the accounts are taken into account. It is possible to filter the results to show only the changes since a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `teamgroupscs360detail`
- **Name:** Team AD groups analysis
- **Description:** This report lists the Active Directory groups of team members in a form of a pivot table. Only active accounts are taken into account. Only the groups directly associated with the accounts are taken into account. It is possible to filter the results to show only the differences compared to a given date. It is possible to modify the columns or to export the results by doing This report lists the Active Directory groups of the team members. Only active accounts are taken into account. Only the groups directly associated to the accounts are taken into account. It is possible to filter the results to show only the differences compared to a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `shareaccessrights360detail`
- **Name:** Managed shares access rights list
- **Description:** This report presents the list of managed shares. It is possible to filter the results to show only changes from a given date. It is possible to modify the columns or export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `teamaccessrights360csdetail`
- **Name:** Team access rights analysis
- **Description:** This report lists the access rights of team members in a form of a pivot table. Only active accounts are taken into account. Only rights directly assigned to users are displayed. Only the rights of type 'Application profile' are taken into account. It is possible to choose to display only the direct team or the whole team. It is possible to filter the results to display only the differences compared to a given date. It is possible to modify the columns or export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `folderaccessrightscs360detail`
- **Name:** Managed folders access rights analysis
- **Description:** This report lists permissions for managed directories in a form of a pivot table. It is possible to filter the results to highlight changes. It is possible to modify the displayed columns or export the results, right click on the table to do so.

---

- **Type:** identity
- **Page:** `teamfolderrights360d`
- **Name:** Team folders rights list
- **Description:** This report lists the folders rights of the team members. Only active accounts are taken into account. It is possible to limit the display to the direct team or to display the whole team. It is possible to display only the differences from a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `permaccessrights360csdetail`
- **Name:** Managed permissions access rights analysis
- **Description:** This report shows the permissions managed by the user as a pivot table. Only active accounts are taken into account. It is possible to filter the results so that only differences from a given date are shown. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `organisationaccounts360csdetail`
- **Name:** Managed organisations accounts analysis
- **Description:** This report lists active accounts of the managed organisations in a pivot table format. It is possible to choose either the direct members of the organisations or all members. It is possible to configure the columns or to export the results by right-clicking.

---

- **Type:** identity
- **Page:** `teamaccessrights360detail`
- **Name:** Team access rights list
- **Description:** This report lists the access rights of team members. Only active accounts are taken into account. Only rights directly assigned to users are displayed. Only the rights of type 'Application profile' are taken into account. It is possible to choose to display only the direct team or the whole team. It is possible to filter the results to display only the differences compared to a given date. It is possible to modify the columns or export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `teamgroups360detail`
- **Name:** Team AD groups list
- **Description:** This report lists the Active Directory groups of team members. Only active accounts are taken into account. Only the groups directly associated with the accounts are taken into account. It is possible to filter the results to show only the differences compared to a given date. It is possible to modify the columns or to export the results by doing This report lists the Active Directory groups of the team members. Only active accounts are taken into account. Only the groups directly associated to the accounts are taken into account. It is possible to filter the results to show only the differences compared to a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `organisationaccessrights360detail`
- **Name:** Managed organisations access rights list
- **Description:** This report lists the access rights related to the managed organisations. Only active accounts are taken into account. Only the 'application profiles' directly associated with the accounts are taken into account. It is possible to choose direct members only or all members. It is possible to display only the differences since a given date. It is possible to modify the columns or export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `teamtimeline`
- **Name:** Team timeline
- **Description:** This report presents the evolutions that have occurred over time. The timeline presents the different timeslots as well as the major events that occurred at each loading. It is possible to select a date to display the details of the identified changes. It is also possible to select a time range by pressing the Ctrl key and clicking on two dates in the timeline.

---

- **Type:** identity
- **Page:** `organisationreports360csdetail`
- **Name:** Managed organisations team analysis
- **Description:** This report lists the active members of the managed organisations in a form of a pivot table. It is possible to filter the results to show only the differences since a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `permaccessrights360detail`
- **Name:** Managed permissions access rights list
- **Description:** This report shows the permissions managed by the user. Only active accounts are taken into account. It is possible to filter the results so that only differences from a given date are shown. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `teamreports360csdetail`
- **Name:** Team analysis
- **Description:** This report lists the active members of the team as a pivot table. It is possible to restrict the display to the direct team or to display the whole team.  It is possible to filter the results to show only the differences since a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `teamfolderrightscs360d`
- **Name:** Team folders rights analysis
- **Description:** This report lists the folders rights of the team members in a form of a pivot table. Only active accounts are taken into account. It is possible to limit the display to the direct team or to display the whole team. It is possible to display only the differences from a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `groupsmembers360csdetail`
- **Name:** Managed groups analysis
- **Description:** This report presents active accounts of the managed groups in the form of a pivot table. All accounts that are members of the group(s) are displayed, whether or not they are direct members of the groups. You can restrict the display to a single group. it is possible to identify only the changes made since a given date. the columns displayed are configurable and the results can be exported, right-click on the table to do so.

---

- **Type:** identity
- **Page:** `access360r_identity_groups`
- **Name:** Groups list
- **Description:** This report lists the user groups. It is possible to filter the results in order to retrieve only the groups directly associated with the user or all the groups; it is also possible to filter the groups by repository; it is finally possible to identify only the changes made since a given date. The columns displayed are configurable and the data can be exported. To do so, right click on the report.

---

- **Type:** identity
- **Page:** `organisationfolderrights360d`
- **Name:** Managed organisations folders rights list
- **Description:** This report lists the folder rights related to the managed organisations. Only active accounts are taken into account. It is possible to choose direct members only or all members. It is possible to display only the differences since a given date. It is possible to modify the columns or export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `appaccessrights360detail`
- **Name:** Managed applications access rights list
- **Description:** This report lists the access rights of managed applications. Only active accounts are taken into account. Only the rights directly associated with the accounts and of type 'application profile' are taken into account. It is possible to identify only changes that have occurred since a given date. It is possible to modify the columns or export the data by right-clicking on the table.

---

- **Type:** identity
- **Page:** `teamaccounts360detail`
- **Name:** Team accounts list
- **Description:** This report lists the accounts of the team members. Only active accounts are taken into account. It is possible to choose to display only the direct team or the whole team. It is possible to filter the results to display only the differences compared to a given date. It is possible to modify the columns or export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `appaccessrights360csdetail`
- **Name:** Managed applications access analysis
- **Description:** This report lists the access rights of managed applications in a form of a pivot table. Only active accounts are taken into account. Only the rights directly associated with the accounts and of type 'application profile' are taken into account. It is possible to identify only changes that have occurred since a given date. It is possible to modify the columns or export the data by right-clicking on the table.

---

- **Type:** identity
- **Page:** `organisationgroups360detail`
- **Name:** Managed organisations AD groups list
- **Description:** This report lists the Active Directory groups of the members of the managed organisations. Only active accounts are taken into account. Only the groups directly associated with the accounts are taken into account. It is possible to filter the results to show only the changes since a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `organisationfolderrightscs360d`
- **Name:** Managed organisations folders analysis
- **Description:** This report lists the folders rights related to the managed organisations in a form of a pivot table. Only active accounts are taken into account. It is possible to choose direct members only or all members. It is possible to display only the differences since a given date. It is possible to modify the columns or export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `access360r_identity_folderrights`
- **Name:** folders rights list
- **Description:** This report lists the user's desktop access rights only the user's active accounts are taken into account. It is possible to filter the results by tree depth. It is possible to identify only the changes made since a given date. The columns displayed are configurable and the results can be exported, right click on the table to do so.

---

- **Type:** identity
- **Page:** `teamaccounts360csdetail`
- **Name:** Team accounts analysis
- **Description:** This report lists the accounts of the team members in a form of a pivot table. Only active accounts are taken into account. It is possible to choose to display only the direct team or the whole team. It is possible to filter the results to display only the differences compared to a given date. It is possible to modify the columns or export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `organisationaccounts360detail`
- **Name:** Managed organisations accounts list
- **Description:** This report lists active accounts of the managed organisations. It is possible to choose either the direct members of the organisations or all members. It is possible to configure the columns or to export the results by right-clicking.

---

- **Type:** identity
- **Page:** `groupsmembers360detail`
- **Name:** Managed groups members list
- **Description:** This report presents active accounts of the managed groups in the form of a table. All accounts that are members of the group(s) are displayed, whether or not they are direct members of the groups. You can restrict the display to a single group. it is possible to identify only the changes made since a given date. the columns displayed are configurable and the results can be exported, right-click on the table to do so.

---

- **Type:** identity
- **Page:** `folderaccessrights360detail`
- **Name:** Managed folders access rights list
- **Description:** This report lists permissions for managed directories. It is possible to filter the results to highlight changes. It is possible to modify the displayed columns or export the results, right click on the table to do so.

---

- **Type:** identity
- **Page:** `organisationreports360detail`
- **Name:** Managed organisations team list
- **Description:** This report lists the active members of the managed organisations. It is possible to filter the results to show only the differences since a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `bwa360_identitysodmatrix`
- **Name:** SoD defects matrix
- **Description:** This report provides a summary of the segregation of duties (SOD) control deviations found for this individual. The gaps are presented in the form of a SOD matrix. The background color represents the level of risk associated with the control. It is possible to analyze the permissions involved by clicking on the relevant activities (rows or columns).

---

- **Type:** identity
- **Page:** `repoaccounts360detail`
- **Name:** Managed repositories accounts list
- **Description:**  This report presents the list of active accounts in the managed repositories. It is possible to filter the results to show only the changes since a given date. It is possible to modify the columns or to export the results by right-clicking on the table.

---

- **Type:** identity
- **Page:** `identitytimeline`
- **Name:** Identity timeline
- **Description:** This report presents the evolutions that have occurred over time. The timeline presents the different timeslots as well as the major events that occurred at each loading. It is possible to select a date to display the details of the identified changes. It is also possible to select a time range by pressing the Ctrl key and clicking on two dates in the timeline.

---

- **Type:** identity
- **Page:** `shareaccessrights360csdetail`
- **Name:** Managed shares access rights analysis
- **Description:** This report presents the list of managed shares in a form of a pivot table. It is possible to filter the results to show only changes from a given date. It is possible to modify the columns or export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `organisationaccessrights360csdetail`
- **Name:** Managed organisations access analysis
- **Description:** This report lists the access rights related to the managed organisations in a form of a pivot table. Only active accounts are taken into account. Only the 'application profiles' directly associated with the accounts are taken into account. It is possible to choose direct members only or all members. It is possible to display only the differences since a given date. It is possible to modify the columns or export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `access360r_identity360`
- **Name:** 360° view of the identity
- **Description:** This report presents all user accesses in the form of a network-like graph. It is possible to display both structured and unstructured rights. It is possible to filter the display on accounts, applications and shares. It is possible to display item details.

---

- **Type:** identity
- **Page:** `teamreports360detail`
- **Name:** Team list
- **Description:** This report lists the active members of the team. It is possible to restrict the display to the direct team or to display the whole team.  It is possible to filter the results to show only the differences since a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** identity
- **Page:** `access360r_identity_accessrights`
- **Name:** access rights list
- **Description:** This report lists the user's application access rights. Only the 'application profile' type rights directly associated with the user are taken into account. Only the user's active accounts are taken into account. It is possible to identify only the changes made since a given date. The columns displayed are configurable and the results can be exported; right-click on the table to do so.

---

- **Type:** organisation
- **Page:** `access360r_organisation_groups360cs`
- **Name:** groups analysis
- **Description:** This report lists the membership groups of the organisation in the form of a pivot table. Only active accounts are taken into account. It is possible to list only direct groups or all groups. It is possible to limit the results to direct members or to display all members. It is possible to filter the results to show only the differences since a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** organisation
- **Page:** `access360r_organisation_sharemap`
- **Name:** Shares map
- **Description:** This report presents the applications accessible by the members of the organisation in the form of a treemap. The size of the blocks can either be proportional to the number of accounts, inversely proportional to the number of accounts or identical. Only active accounts are taken into account. It is possible to restrict the display to direct members or to display all members. It is finally possible to display application details by clicking on the blocks.

---

- **Type:** organisation
- **Page:** `bwa360_organisationsodmatrix`
- **Name:** SoD defects matrix
- **Description:** This report provides a summary of the segregation of duties (SOD) control deviations found for this organisation. The gaps are presented in the form of a SOD matrix. This analysis includes both the organisation and the sub-organisations. The background color represents the level of risk associated with the control. It is possible to analyze the permissions involved by clicking on the relevant activities (rows or columns).

---

- **Type:** organisation
- **Page:** `access360r_organisation_applicationrights360cs`
- **Name:** application analysis
- **Description:** This report lists the organisation's members access rights at an application level in the form of a pivot table. Only active accounts are taken into account. It is possible to restrict the display to direct members or to display all members. It is possible to display only the differences from a given date. It is possible to modify the columns or to export the results by right-clicking on the table.

---

- **Type:** organisation
- **Page:** `organisationtimeline`
- **Name:** Organisation timeline
- **Description:** This report presents the evolutions that have occurred over time. The timeline presents the different timeslots as well as the major events that occurred at each loading. It is possible to select a date to display the details of the identified changes. It is also possible to select a time range by pressing the Ctrl key and clicking on two dates in the timeline.

---

- **Type:** organisation
- **Page:** `access360r_organisation_applicationmap`
- **Name:** Applications map
- **Description:** This report presents the applications accessible by the members of the organisation in the form of a treemap. The size of the blocks can either be proportional to the number of accounts, inversely proportional to the number of accounts or identical. Only active accounts are taken into account. It is possible to restrict the display to direct members or to display all members. It is finally possible to display application details by clicking on the blocks.

---

- **Type:** organisation
- **Page:** `access360r_organisation_folderrightscs360`
- **Name:** data access analysis
- **Description:** This report lists the folder access rights of the organisation's members in the form of a pivot table. Only active accounts are taken into account. It is possible to restrict the display to direct members or to display all members. It is possible to display only the differences with respect to a given date. It is possible to modify the columns or to export the data by right clicking on the table.

---

- **Type:** organisation
- **Page:** `access360r_organisation_accessrights360cs`
- **Name:** access analysis
- **Description:** This report lists the organisation's members access rights in the form of a pivot table. Only active accounts are taken into account. Only the rights directly associated with individuals are taken into account. Only the rights of type 'Application profile' are taken into account. It is possible to restrict the display to direct members or to display all members. It is possible to display only the differences from a given date. It is possible to modify the columns or to export the results by right-clicking on the table.

---

- **Type:** organisation
- **Page:** `access360r_organisation_groups360`
- **Name:** Groups list
- **Description:** This report lists the membership groups of the organisation. Only active accounts are taken into account. It is possible to list only direct groups or all groups. It is possible to limit the results to direct members or to display all members. It is possible to filter the results to show only the differences since a given date. It is possible to modify the columns or to export the results by right clicking on the table.

---

- **Type:** permission
- **Page:** `permissiontimeline`
- **Name:** Permission timeline
- **Description:** This report presents the evolutions that have occurred over time. The timeline presents the different timeslots as well as the major events that occurred at each loading. It is possible to select a date to display the details of the identified changes. It is also possible to select a time range by pressing the Ctrl key and clicking on two dates in the timeline.

---

- **Type:** permission
- **Page:** `access360r_permission_analytics`
- **Name:** self-service analytics
- **Description:** This report presents the access rights of the permission in the form of a dynamic pivot table where it is possible to select the analysis dimensions. Only active accounts are taken into consideration. it is possible to identify only the changes made since a given date. the columns displayed are configurable and the results can be exported, right-click on the table to do so.

---

- **Type:** permission
- **Page:** `access360r_groupsubpermissions360`
- **Name:** 360° view of the sub-permissions
- **Description:** This report presents the sub-groups of the group in the form of a network graph. The direction of the arrow means 'is in'. It is possible to display the details of the groups.

---

- **Type:** repository
- **Page:** `access360r_repository_groupanalytics`
- **Name:** self-service groups analytics
- **Description:** This report presents the accounts in the form of a dynamic pivot table where it is possible to select the analysis dimensions. Only active accounts are taken into consideration. it is possible to identify only the changes made since a given date. the columns displayed are configurable and the results can be exported, right-click on the table to do so.

---

- **Type:** repository
- **Page:** `access360r_repository_accountanalytics`
- **Name:** self-service accounts analytics
- **Description:** This report presents the accounts in the form of a dynamic pivot table where it is possible to select the analysis dimensions. it is possible to identify only the changes made since a given date. the columns displayed are configurable and the results can be exported, right-click on the table to do so.

---

- **Type:** repository
- **Page:** `repositorytimeline`
- **Name:** Repository timeline
- **Description:** This report presents the evolutions that have occurred over time. The timeline presents the different timeslots as well as the major events that occurred at each loading. It is possible to select a date to display the details of the identified changes. It is also possible to select a time range by pressing the Ctrl key and clicking on two dates in the timeline.

---

- **Type:** repository
- **Page:** `access360r_repository_similargroup`
- **Name:** Similar groups analytics
- **Description:** This report allows you to analyze the similarities between groups. A calculation is performed to identify the number of active accounts in common between the groups. The results are presented in the form of a pivot table. Only direct groups assignments are taken into consideration. It is also possible to present the results in a list format in order to facilitate the export of results. Regardless of the display mode selected, it is possible to obtain details on the 'application profiles' as well as to identify the common accounts and the specific accounts of each profile.

---

- **Type:** repository
- **Page:** `access360r_repository_reconciliation`
- **Name:** Orphaned account reconciliation management
- **Description:** This report presents the orphaned accounts of the repository. Only active accounts are taken into account. A summary table shows the reconciliation status and the trend. A detail page allows you to process orphaned accounts. It is possible to reconcile the accounts one by one either by associating them with their owner, by indicating that their owner is no longer part of the company, or by marking them as service accounts.

---

- **Type:** repository
- **Page:** `access360r_repository_filesources`
- **Name:** Files used to fulfill the ledger
- **Description:** This report lists the source files used to consolidate information about this repository. Note that it is possible for internal technical configuration reasons that only some of the files used are listed here. In case of doubt, we invite you to contact the platform administrator who has the complete list and will be able to give you more information.

---

- **Type:** share
- **Page:** `access360r_share_analytics`
- **Name:** self-service analytics
- **Description:** This report presents the access rights of the share in the form of a dynamic pivot table where it is possible to select the analysis dimensions. it is possible to identify only the changes made since a given date. the columns displayed are configurable and the results can be exported, right-click on the table to do so.

---

- **Type:** share
- **Page:** `access360r_share_accessrights360cs`
- **Name:** access analysis
- **Description:** This report presents the access rights to the content of the share in the form of a pivot table. Only active accounts are taken into account. It is possible to display only the differences with respect to a given date. It is possible to modify the columns or export the results by right-clicking on the table.

---
