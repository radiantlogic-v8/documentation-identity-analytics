---
title: "Identity Analytics Access Review Guide"
description: "Identity Analytics Access Review Guide"
---

# My First Review

Through this chapter we will guide you to configure and operate your first access certification review with a typical example.

Five types of review can be configured:  
Five types of review can be configured:

- Repository accounts review, to review all accounts in the selected repositories,
- Group membership review, to review all group and their member accounts in the selected repositories,
- Application access rights review, to review all access rights in the selected applications,
- Server access rights review, to review all access rights in the selected servers,
- Safe permissions review, to review all access rights in the selected CyberArk PAM Safes if you have enabled PAM Booster.

> For Server review, the Server access rights need to be uploaded in the identity ledger as permissions and servers as application of type server. You can use for windows servers the add-on extracting windows local accounts and groups bw_winlocalresources available on the [Radiant Logic support site](https://files.radiantlogic.com/receive/?packageCode=IX0qTSRyilShjhpxusLWpUDzzb4rduq2tO9F81NhEt4) (Home > Customer Downloads > Facets > bw_winlocalresources). This add-on collect and map the extracted data as well in the Identity Analytics.

In this chapter, we will configure and launch an application access rights review. The repository accounts review, group membership review and server review use the same principles, and a dedicated documentation is also available for the PAM Booster designed for CyberArk.

> As a reminder in IAP version 2.2 a new "sign off" principle has been added to the review process, as well as the the ability to launch the remediation process as soon as the reviewer signs off.

> In IAP version 3.0, "review campaigns" was introduced, providing enhanced capabilities to configure, schedule, and manage campaign-related notifications. These features are available through the new Review Campaign Management interface. The previous Review Management interface, which contained finalized reviews from earlier versions, has been renamed as **Custom Review Management**.
Due to these changes, it is **required** to finalize all web-based reviews before upgrading to IAP version 3.0.

![](./media/newcampaign.png)

## Use Case Description

The ACME company is a mid-sized company of roughly 1000 people, they are operating in the US and ran public last year. Therefore they need to comply with SOX constraints. As part of this, their finance systems must be reviewed on a quarterly basis to ensure that access rights are properly configured.

Financial systems are made of three applications:

- Elyxo-Treasury
- SAGE-Accounting
- SAP

In the following chapters, we will discover how to configure and operate an access certification campaign as well as the remediation process to comply with SOX on this perimeter.

We consider that data has already been loaded and correlated:

- Identities are loaded
- Line managers are loaded
- Elyxo-Treasury, SAP and SAGE-Accounting applications are loaded and accounts are reconciled with their respective owners
- Application managers are configured (both business owners and technical owners)

## Step 1 - Define the Review Perimeter

### Applications to review

The first step "1. Review Perimeter" is to define the review campaign perimeter: what needs to be reviewed.
In our context we want to review ALL access rights on the following applications:

- Elyxo-Treasury
- SAGE-Accounting
- SAP

To do so, you have to choose the applications to review using two different methods, "Static Selection" or "Selection by Tags".
The first method is to pick in the list the applications, which means here to select SAGE-Accounting, Elyxo-Treasury and SAP applications:

![](./media/IAP142.png)

The second method consist of using tags, which could be very useful when the number of applications to select is high, and when new SOX applications will be added to Identity Analytics in the future. In that case, you will not have to reconfigure you campaign. In the example below, we are using tags ISO27002 and SOX to choose the three required applications:

![](./media/IAP141.png)

Note that when using tags, filtering the table by column has no effect on the perimeter. Only the filter to the right of "Selection by Tag" does.

Please note, six steps are required to configure a review campaign:

1. The first step `Review Perimeter` allows to define your review perimeter,
2. The second step `Review Strategy` helps you define the review strategy,
3. The third step `Perimeter Preview` shows the data for the review on the current timeslot,
4. The fourth step `Reviewer UI` allows to configure the reviewer user interfaces,
5. The fifth step `Campaign Schedule` helps you define the scheduling strategy,
6. The final step `Campaign Information` concerns review campaign information.

ALL selected data MUST be reviewed, the _reviewer_ is automatically identified based on the entries to be reviewed as configured in the second step "2. Review Strategy".  
For example, a strategy could be:

- user accounts are reviewed by the line manager,
- technical are reviewed by the application owner,
- all other account and if no line manager and no application owner are found, the default reviewer is taken.

> For reviews on large volumes of data, above 30,000 entries by default, step 3 `Perimeter Preview` is deactivated to smooth the experience, and the KPIs in step 6 are hidden. As a result, the campaign is forced into "on hold" mode to allow perimeter review from the campaign management interface before launching the reviews. This threshold of 30,000 entries can be modified in the project's technical configuration using the variable `ias_reviewdisablepreviewlimit`.

### Accounts Review Perimeter

To refine the review perimeter, the advanced mode in the first step allows you to include or exclude some types of accounts. For example: User accounts, technical accounts, orphaned accounts and leaver accounts.

![](./media/IAP143.png)

You can configure that only some accounts will be part of the review, either by playing with the options (user accounts, orphaned accounts, ...) or by tagging the accounts you want to include in your review thanks to the account search interface.

This is super flexible as it can be for instance used to review only accounts with some attributes or characteristics such as:

- Accounts from people working in a given division / country / ...
- Accounts with a given sensitivity level,
- Accounts with given controls defects,
- ...

In addition, You can filter accounts using saved rules.

![](./media/IAP143-1.png)

Two possibilities for that, you can use predefined rules available in the project or define your own rule from the user interface as in the following screenshot. In the first case, the list of related rules will be displayed in the combo box "Select Custom Perimeter Rule". The rules defined in the project have to get the following values for:

- Tag > "family" attribute: "Perimeter",
- The option Execution plan > "Include in execution plan" selected.

Your rule will be executed and the result stored in the database during the next data upload. You can also using the tab "History" of the rule, add it manually to existing timeslots if you are connected to the database.

If the expected rule is not available or does not suite the end-user needs, he can create it directly from the web interface by clicking on the three small dots to the right of the field and then "Create rule...". Several rules can be created, but only one can be selected at a time:

Select an available rule:  
![](./media/IAP143-4.png)

Create a new rule:  
![](./media/IAP143-5.png)

![](./media/IAP143-2.png)

Once your criteria are entered in the rule builder, click on the magnifying glass to display the result, then give it an understandable name and click on save to save the rule.

![](./media/IAP143-3.png)

Using this method allows for example to filter only:

- accounts having access to a list of specific applications,
- accounts from a specific list of repositories with a max risk level higher than 2,
- accounts from a specific repository having a direct access to a list of specific permissions,
- accounts belonging to identities working in a list of specific departments (organizations), and so on.

In our use case we want to review **ALL** accounts, so lets keep the default configuration.

### How to Tag Accounts and Permissions

- Tag Accounts

To identify some specific accounts or some specific permissions, creating tags allows you to filter on them. Creating tags should be done before the review configuration.

For example, to create a tag and filter on accounts that contain "adm" in their login to select most of the administration accounts, go to account search pages and enter in the smartsearch the rule that correspond to your need. And click on "Bulk add a tag in search results" to create your new tag. This new tag can be use to refine the perimeter of your review.

![](./media/IAP144.png)

- Tag Permissions

Once again you can refine your review perimeter in this section by selecting only some permissions to review. In order to do so, you have to tag the permissions that will be part of the review perimeter thanks to the permission search interface.

This is super flexible as it can help you to review only some permissions such as:

- Sensitive permissions
- Permissions with given controls defects
- Admin permissions
- ...

Keep in mind that at the end the review configuration, only the lines whom **BOTH** accounts and permissions that are part of the perimeter will be part the review. In that case, the resources that are reviewed (the Elyxo-Treasury, SAP and SAGE-Accounting applications in our case here) will not be considered compliant at the end because the review is not comprehensive.

In our use case we want to review **ALL** permissions, so lets leave this part empty.

## Step 2 - Define Review Strategy

In this step, you'll find two parts: the reviewer strategy and the AI options.

### Reviewer Strategy

This section helps you to further refine the _reviewer_ strategy.

RACI principle is enforced, as a result there is only **ONE** _reviewer_ accountable for each entry to review.

- In case of several application owners configured in the system, only one application owner is picked (the one who is not 'delegated')
- In case of several direct line managers configured in the system, only one direct line manager is picked. Keep in mind that as a best practice, **DO NOT** configure several direct line managers in your system as it could lead to duplicated lines in some analytics

In the Application Access Right review, you have the choice between the following strategies:

- User Accounts by Line Manager and Technical Accounts by Application Owner
- User Accounts by Line Manager and Technical Accounts by Technical Account Owner
- User Accounts by Line Manager and All Other Accounts by Application Owner
- User Accounts by Account Owner and All Other Accounts by Application Owner
- All Accounts by Application Owner
- All Accounts by Default Reviewer

![](./media/IAP146.png)

You can make application owners review **ALL** the accounts, including user accounts.

This can be useful if for instance you need to review "privileged permissions" such as admin access rights granted to admin user accounts (accounts whom login is starting with \_adm\_\_ for instance). In this particular use case, you will most probably want to have those accounts reviewed by the application owner instead of the IT department line manager of the user accounts owners.

Finally you can configure a _default reviewer_ which will be used when no valid _reviewer_ is found for a given entry.
This is the case if:

- A user account owner does not have any direct line manager
- The user account owner is no longer part of the company
- The user account owner does not have an email address
- An application does not have any business owner
- The application business owner is no longer part of the company
- The application business owner does not have an email address

As a best practice this parameter should not be used during the review, you should instead ensure that all entries have a valid "manager" by performing a data quality check prior to launch your review campaign.
As you will see, if RadiantOne Identity Analytics does not find any reviewer for a given line, it will be highlighted in the next section and you won't be able to start your review campaign.

Let's keep the default values for now and let's move to the next section.

### Advanced Reviewer Strategy

#### When configuring a new campaign

Clicking on "Advanced" allows you to select an advanced reviewer policy template from the combo box. You can use as it is or if you're a technical administrator modify it specifically for your campaign by clicking on "Edit Reviewer Policy" and modifying the script.

![](./media/IAP146-1.png)

![](./media/IAP146-2.png)

#### How to manage reviewer policy templates

From the campaign manager, on the top right of the page, a tab "Reviewer Policies" allows technical administrators to create and manage script templates per review type that will be available each time a new campaign is created or modified.

![](./media/IAP146-3.png)

![](./media/IAP146-4.png)

For example, if you want to set the following strategy:

- User accounts by themselves
- Service accounts by account managers
- All other accounts by application owner
- Default reviewer for left entries

You'll have to enter in the script the following conditions:

```javascript
if (accounttype.equals("user")) {
  ("myself");
}
if (accounttype.equals("service")) {
  ("accountowner");
}
("default.applicationowner");
```

This will ease the configuration of new campaigns when the review policies are specific to the organization.

### AI Options

#### AIDA (SaaS only)

When using our SaaS offer with AI enabled, you can activate the Artificial Intelligence Data Assistant AIDA for each campaign. AIDA will assist the reviewers when performing the review if he asks for it.

![](./media/IAP243.png)

Note that AIDA is only available for Application Access Rights type of reviews for now, and will be extended to other types of reviews and other RadiantOne solutions and features in the future.

The end-user can enable the prompt provided by AIDA by turning on the option “Enable AIDA Prompt”.

![](./media/IAP277.png)

By doing so, at any time the reviewer can ask AIDA questions at the bottom of the side panel:

![](./media/IAP278.png)

AIDA with User Access Reviews follows these four main principles:

1. AIDA guides the reviewer through the review process, step by step, so that the reviewer is clear about where to start, time is saved and the reviewer has a better understanding of the data.
2. At each stage, AIDA proposes a decision based on the analysis it has carried out, explaining why this decision should be made by presenting the analysis. The reviewer then has the information needed in order to proceed in his decision-making process.
3. Once the reviewer makes his decision, AIDA will carry out the action for him in the system. This method aligns with compliance regulations because it is mandatory that a human being, and not a machine, be the one to fully perform the review.
4. During the review process and in addition to AIDA's suggestions and explanations, the reviewer can delve more deeply by using Large Language Models (LLM) to request further clarification and analysis which helps to explain the context (who can access what, what is the access chain, how to compare accesses, etc.).

#### Decision History

Also called "Incremental Review", this option will help you to leverage previous access certification campaigns.
When enabled, previous review status will be used to "prefill" review status and review comment.

This happens **only** when:

- The entry has been reviewed in the configured timeframe (_A valid entry is an entry which has been reviewed in the last X days_)
- In case of an user account, account owner characteristics have not changed since the last review:
  - Organisation
  - Job Title
  - Internal status

![](./media/image7bis.png)

You can also chose to simply remove those entries from the review perimeter if needed (if for instance you only want to review changes that occurred since the last review date, without displaying valid entries)

We won't use this feature for now as it is our very first access review campaign, so let's keep the default values for now and move to the next section by clicking on the _Next_ button

![](./media/image7.png)

## Step 3 - Perimeter Preview

This section will present a preview of the data to be reviewed as well as the _computed reviewer_ for each entry.

![](./media/IAP147.png)

> Creating and launching a review on a previous timeslot is not a standard use case, so the preview shown in the review campaign setup only gives general information based on the last timeslot. The preview based on the timeslot you selected will be available once the campaign is created by entering the details of your access review (see Campaign Follow-up section). This is why we recommend that you configure your campaign “on hold” if it is a scheduled campaign at step 6 of the configuration wizard.

You can browse through the table, reorder the columns, add or remove columns through the options or export the data in CSV/excel format if needed. Click on the three buttons on the upper right of the table for such purpose.

![](./media/IAP148.png)

When configuring columns:
![](./media/IAP148bis.png)

You can also use the filtering capabilities at the top of the table such as the filter per reviewer on the upper left of the table or the global filter and the group by feature on the upper right.
![](./media/IAP151.png)

You can access to objects details by clicking on the corresponding labels (login, name, permission, ...)

![](./media/IAP149.png)

If some _reviewers_ have not been found an error message is displayed on the screen and the _Next_ button is disabled. click on the _Back_ button and refine your configuration by adding the missing managers to solve this problem. This may occur only when using "advanced mode" with the script, since by default, when the reviewer is not found, the default reviewer is set as reviewer.

![](./media/IAP150.png)

You still can browse the table to check each entry.  
If everything is ok, you can click on _Next_ to move forward.

> **Note** For reviews on large volumes of data, above 30,000 entries by default, this step is deactivated to smooth the experience. In that case, the following message will be displayed:

![](./media/IAP276.png)

## Step 4 - Reviewer UI

In this step you can specify the user interfaces you want to provide to the reviewers.

![](./media/IAP244.png)

The first section focus on the selection of attributes to include and display or hide in the reviewer table.

![](./media/IAP244-1.png)

By clicking on "Select Columns", you can choose the attributes you want to include by moving the from the left to the right of the table. By activating the "eye" icon, you choose to display the attribute by default in the table, by deactivating it you choose to hide it. You can also re-order the the attributes as you wish.

![](./media/IAP244-2.png)

The tab "Customization" allows you to rename the attributes with an understandable label to make it easier for reviewers to understand.

![](./media/IAP244-3.png)

The second section focus on the reviewer decision configuration: revoke, validate, update entries.

![](./media/IAP244.png)

You can make comments mandatory when the `Approve` button is used.
You can modify (add or remove) the default comment list for `Revoke` and `Update` actions, and also add your own new comments if needed.
By default, the following comments are proposed for `Revoke`:

![](./media/IAP245.png)

By default, the following comments are proposed for `Update`:

![](./media/IAP246.png)

If you want to avoid the "Rubber Stamping" effect, you can limit the bulk actions of the reviewer to a certain number of entries.

Four additional options can be disabled such as:

- allowing the reviewer to specify that he is not the right person with the `I'm not the reviewer` button. In that case the related entries are set as "to reassign" and are not visible any more by the reviewer. The accountable reviewer has to change. The review owner has then to re-assign those entries to another person from the follow-up interfaces of the review instance.
- allowing the reviewer to `ask for help to`another person in his team if he is line manager, or another owner if he is a resource owner. In that case, the reviewer stay the accountable reviewer of the entries, however he ask to a responsible reviewer to take the decisions on his behalf for the selected entries.
- allowing the reviewer to `hide already reviewed entries by default`: when activated, the reviewer will only see by default the remaining entries he has to review. He still can uncheck this option on top of the tables to see all entries, including the one already reviewed.

- allowing the reviewer to `Hide delegated entries by default`: when activated, the reviewer will only see by default his remaining entries but not the one he has delegated to other people. He still can uncheck this option on top of the tables to see all entries, including the one he has delegated.

In your case, you can keep the default values and click on _Next_ to move forward.

## Step 5 - Campaign Schedule

This part allows you to configure the schedule of your review instances and the email notification and reminder strategies.

![](./media/IAP247.png)

> Please note that the `Timeline` and `Calendar` widgets are hidden when the `Manual` mode is selected - this is because there is no campaign start date yet.  
> But `initial` and `reminder` notifications will be sent nonetheless for campaigns launched manually, according to the schedule configuration.

### Campaign Scheduling

In the first section, `Campaign Scheduling`, you can choose either to define a **manual** or a **scheduled** campaign.

If you choose the **manual** option, the review instance must be launched by the campaign owner when needed. You need to specify the expected duration of the campaign in days, so that notification of completion of the review instance is automatically sent to the campaign owner on the correct date, **as well as reminders** according to the reminder strategy you define in the next section.

If you choose the **scheduled** option, the first review instances will be launched automatically at the **initial start date** you've specified. Then the next instances will be launched based on the frequency you've defined, which could be weekly, monthly, quarterly, semi-annual, yearly. You have also to set the expected duration of the campaign in days, so that notification of completion of the review instance is automatically sent to the campaign owner on the correct date, as well as reminders according to the reminder strategy you define in the next section.  
You can also activate a reminder to notify the campaign owner a certain number of days, which you can define, before the campaign automatically starts. The aim is to allow the owner to review the scope and reviewers to be called upon before the review instance starts.

The finalization of **manual** and **scheduled** review instances is therefore manual, allowing the campaign owner to grant a grace period if necessary, to ensure that all reviewers have completed their review.

For both **manual** and **scheduled** campaigns you can check the option "Put on hold at startup" so that when the review will start either automatically or manually, the review instance will be in pause status and the notifications will not be send, allowing you to review the scope and the reviewer strategy before starting it. In your case we will check that option, to review the perimeter before launching the first instance.

In your case here, you can choose a "scheduled" review with a quarterly frequency and keep the default options. In addition, check the "Put on hold at startup" box so that you can log in and check the perimeter before starting the review and sending related notifications.

### Reviewers' Notifications and Reminders Strategies

In this section, you can activate initial notifications and reminders sent to reviewers. For each of these, you can edit the e-mail templates and modify them as required in the three languages supported by default: English, French, Spanish. Those templates are used when notifications are send automatically and also when the campaign owner wants to send reminders manually to a selection of reviewers from the follow-up interface.

![](./media/IAP248.png)

You can choose pre-defined template by selecting one in the dropbox "Email Template" and then modify it specifically for your review. On the right, the name of the original template use is displayed.

When editing email templates, you can use the gear icons to insert variables in the main text of the email or in the fields of the destination email address.

![](./media/IAP249.png)

As far as reminders are concerned, you can set the frequency of notifications by determining after how many days you wish to send the first reminder, and how often you wish to send subsequent reminders. On the right-hand side, you have a graphical representation of this frequency, which you can display in the form of a timeline or calendar.

> The preview is **hidden for manual** campaings, but `initial` and `reminder` emails will be sent nonetheless according to the schedule configuration.

![](./media/IAP250.png)

![](./media/IAP251.png)

Later, once you've finalized the configuration of your campaign, you'll be able to update these reminder dates directly from the campaign management interface, with the option of adding or deleting specific dates.

You can leave the default templates and reminder calendar as they are for your use case.

### How to manage notification templates

From the campaign manager, on the top right of the page, a tab "Mail Templates" allows technical administrators to create and manage notification templates for initial notification and reminder email templates.

![](./media/IAP280.png)

![](./media/IAP280-1.png)

You can create new template, edit and duplicate existing ones, or remove some templates. Deleting templates will not affect any campaigns that have already been set up using those templates.
For each template, you can define emails in english, french and spanish. The Identity Analytics can specify the languages tha need to be supported by setting in the technical configuration of the project the variable `ias_supportedlanguages` to "en,fr,es".

This will ease the configuration of new campaigns to create and share notification templates across user access review campaigns for the organization.

## Step 6 - Campaign Information

You are almost done, the last thing you need is to give additional information to your campaign such as a pretty name, description, specify an owner, a priority level. This priority level can be useful when several review campaigns are being run at the same time, giving your _reviewers_ a way of evaluating their entries by priority level.

![](./media/IAP152.png)

Three additional options are available here, such as "Enable offline mode", which allows reviewers to download the entries to be reviewed into an Excel spreadsheet from their home page and upload it once they have partially or completely completed it. It allows also the campaign owner to send e-mail notifications with this spreadsheet attached so that reviewers can work offline. This option is particularly appreciated when reviewers travel a lot or have no access to the company's IS for whatever reason (if they are contractors for example). Note that a same reviewer can work both online and offline if needed.

The second option `Attach Review to Timeslot` allows to configure user access review in Identity Analytics that are fixed to a specific timeslot, which represents the configuration of the accesses at a particular time. This way, the User Access Review is not taken into account the newer timeslots where some of the entries may have been removed since the review began.

The third option disables the campaign, so that it cannot be launched automatically or manually. You need to edit it and change the deactivation of this setting for it to work. This allows you to work on the configuration at a later date and perform a few additional checks before the review instance starts and notifications are sent automatically.

![](./media/IAP152bis.png)

When offline mode is enabled:

- The reviewer can complete the entries to review on excel file

![](./media/IAP218.png)

- Download and Upload of the excel file can be done:
  - By the _campaign owner_ from the campaign management interface, by clicking on the "Upload" button in the "Latest Review" section on the right:

![](./media/IAP215.png)

- By the _reviewer_ from his home page Access360 interface:

![](./media/IAP155.png)

- When the excel file is uploaded, the number of review entries is displayed:

![](./media/IAP216.png)

- Then the review progress bar is updated:

![](./media/IAP220.png)

Finally, in the "Compliance Framework Specification" section, you can define tags for your campaign to easily filter from the "Review Campaign Management" interface on all campaigns contributing to the same compliance framework, as in this example, filtering campaigns configured in accordance with SOX:

![](./media/IAP252.png)

Once everything is fulfilled, click on **Finish** to save your campaign configuration.

> **Note** For reviews on large volumes of data, above 30,000 entries by default, the KPIs in this step are not displayed to smooth the experience. In addition the campaign is forced into "on hold" mode to allow perimeter review from the campaign management interface before launching the reviews.

## Step 7 - Managing your review campaign

Once your review campaign configuration has been saved, it appears in the compliance review management page.  
You can access to this page through the menu _Review / Review Campaign Management_

![](./media/IAP153.png)

> **Notes:**
> To check the status of your access review campaigns and their review instances, you must be in the latest timeslot, otherwise if you are in a past timeslot, certain review instances may appear active even though they were closed in the current timeslot.

When selecting your campaign in the list, you can either edit the configuration by clicking on **Configure**, **Duplicate** the configuration of your campaign or **Delete** it with all its review instances history.

Additional buttons are available to **Create** new campaigns and **Export Configuration** **Import Configuration** by clicking on the three bullets.

![](./media/IAP253.png)

On the right side of the screen, you'll find all the information regarding the review instances that are pending, in progress or have already been completed. The left section includes two parts, "Latest Review" listing the on-going/active review instance, and "Review History" listing the completed reviews.

![](./media/IAP254.png)

In this case, we get the message "Scheduler not started", which means that you need to activate the scheduler for the review instances to start on the scheduled date. This happens mainly when you start the solution for the first time. To do so, using the left menu bar, go to "Settings" > "System" and then click on the "Scheduler" button:

![](./media/IAP257.png)

Specify the hour you need to start the scheduler, click on "Start Scheduler" and then confirm:

![](./media/IAP256.png)

When the scheduler is started, you'll find in the same page the information about the lifecycle of the scheduler:

![](./media/IAP258.png)

If the campaign has been scheduled which is the case here, back in the review campaign management dashboard, you must wait until the "initial start date" has been reached to see information on the right side. In your case, you have checked the option "Put on hold at startup" in the configuration of the campaign, this means that your review instance will be on pause, so that you have the time to check its perimeter and reviewer strategy based on the current data before starting it. Once the review instance has started, notifications will be sent to all _reviewers_ involved based on the campaign configuration you have defined. On the right you will have the following display wether the review is started or in pause mode:

![](./media/IAP255.png)

The first occurrence of the review will have "#1" added at the end of its name, the second "#2" and so on.
On the active instance, you can:

- go to the follow-up dashboard by clicking on **Details**,

- manage reminders (remove/create) by clicking on **Reminders**,

- pause your instance by clicking on **Pause**,

- finalize your review instance by clicking on **Finalize**,

- when paused, delete your review instance by clicking on **Delete**.

### Campaign Follow-up: **Details** button

The very first thing you will want to do is to go to the follow-up dashboard to check the review perimeter. Select your review campaign and click on the _Details_ button.

#### Measuring review campaign progress

The first tabs "Review Status" and "Review Statistics" allow to measure and follow the progress of your review instance with the help of KPIs and graphs.

![](./media/IAP161.png)

##### Review Status

In the first "Review Status" tab, _Reviewers_ that have already signed off their user access review are shown in the left-hand table. In the table on the right, reviewers who have not yet started reviewing entries, or who are in the process of reviewing them, or who have reviewed all entries but have not yet signed off their review, are displayed.

When you click on the KPI or reviewer name in the tables on this tab, you go directly to the "Entries to review" tab, with the filter applied according to the KPI/reviewer name you initially clicked on.

Note that from the right table, you can send reminders to a selection of reviewers if needed. This is particularly helpful when you have reassignment (accountable or responsible) that have been done recently and when the next reminders won't be coming soon.

When doing so, the reminder email template you configured within your campaign is proposed here, with the ability to change/update the text:

![](./media/IAP259.png)

When offline mode has been activated in the campaign configuration, you can choose also between three different strategies:

- Send a message to the selected _reviewers_ with all the entries as an attachment
- Send a message to the selected _reviewers_ with the remaining entries to review as an attachment
- Send an email to the selected _reviewers_ without attachment

![](./media/IAP263.png)

The first two choices can be useful if you want to send the review content along with the email for instance when you want to enable "offline" reviews by some _reviewers_ (reviewing through an excel spreadsheet instead of reviewing in the UI).
The last one is more "traditional" as they do not include any attachment.

If the offline mode is disabled in your campaign configuration, you cannot add attachment to your notifications.

Depending on your review strategy and your review phase (initial notification,gentle reminder), you have to select the right Mail Strategy in the combo box.

The mails look like:

![](./media/image17.png)

##### Review Statistics

You can also browse through the review statistics to check the current review status in the second tab "Review Statistics".

![](./media/IAP162.png)

But what we're interested in here is more the third tab "Entries to Review", to review and refine reviewers if needed before starting the review.

#### Refine reviewers

In the "Entries to review" tab, you can find all entries with the related reviewers that has been assigned regarding to the review strategy you specified in the campaign configuration.

![](./media/IAP163.png)

If needed, you can add the "Reviewer Origin" column by right clicking in the table, selecting "Configure", and then in the list the related column or any other information you want to display in the table.

![](./media/IAP260.png)

Then use the filtering capabilities if you want to reassign some entries based on reviewer, permissions, or else. When selecting a set of entries, you can:

- Reassign the entries to another reviewer by clicking on **Reassign**,
- Escalate the entry to the manager of the reviewer by clicking on **Escalate**,
- Take a decision on behalf of the reviewer by clicking on the three-point icon then **Force Bulk Approval/Revocation/Update**,
- Reset the decisions taken for the selected entries by clicking on the three-point icon then **Force Bulk Reset**,
- Force the sign off on the selected entries by clicking on the three-point icon then **Force Sign Off**,
- Add/update comment of the selected entries by clicking on the three-point icon then **Force Bulk Comment**,

Finally you have the option by clicking on the three-point icon then selecting **Download All Entries** to download in an excel spreadsheet the who list of entries.

![](./media/IAP261.png)

Note that this table is displaying the first 2,000 entries, so you need to apply filter based on reviewer, accountable manager, application or review status to work on selections of entries.

Once I'm ok with the list of entries and their related reviewers, I can go back to the campaign management interface and start the review by clicking on "Resume":

![](./media/IAP267.png)

Then the review will be displayed as `Active`:

![](./media/IAP268.png)

### Reminders Management: **Reminders** button

The reminder dialog lets you fine-tune the reminders you wish to send during your campaign. It lists all the dates on which reminders will be sent. You can delete or add new reminders.

![](./media/IAP262.png)

In your case, in addition to the default reminders, we've chosen to add two, at one day and four days before the end date.

### Update campaign status: **Pause/Resume**, **Abort** and **Finalize** buttons

At any time while a review is in progress, you can choose to pause it. In this case, reviewers will no longer have access to the review interfaces until you click "Resume" again. This allow you to review again the perimeter if you have any doubt or to remove your review by clicking on the **Delete** button.

The **Finalize** button allows you to end the review instance at any time, even if the reviewers have not completed their reviews. In our case, we'll wait until we receive notification of the "end date" before finalizing.

When a review instance starts, either manually or automatically if programmed, the interrupt button can be used if the startup process takes too long:

![](./media/IAP269.png)

## Step 8 - Reviewing entries

_Reviewers_ have received an email and will connect to the RadiantOne Identity Analytics platform to review their entries. _Reviewers_ have to select the review campaign to review.

![](./media/IAP155.png)

As a _reviewer_ I can approve, revoke or comment one by one, I can also perform bulk operations by selecting several entries at once.

![](./media/IAP156.png)

I can export data when clicking on the advanced options on the right (...) in CSV or XSLX, activate/deactivate advanced filtering and configure columns.

![](./media/image20.png)

When activating the "Advanced filtering" option, I can filter and sort easily some of the columns like in an excel spreadsheet.

![](./media/image20-2.png)

When clicking on "Configure columns", I can reorder the table, add/remove columns or freeze first/last columns.

![](./media/image20-1.png)

As I move forward in my reviews, if I check the option "Hide already reviewed entries", I see the list diminishing: all reviewed entries are no longer displayed in the list.
Nevertheless, I can change my mind and I am allowed to change the review status of any entry until the review campaign is finalized.
In order to do so, I just have to uncheck this option.

![](./media/IAP157.png)

Only the remaining entries to review are displayed.

![](./media/IAP158.png)

I can filter the entries by account, identity, permission or application thanks to the Global Filter.
This is useful if I want to review the entries by Login, Identity, Permission, Service Account, Application, Review Comment and use bulk operations when needed

![](./media/IAP159.png)

Once everything has been reviewed, a pop-up window appears asking me to "sign off" or "display all reviewed entries" if I change my mind and want to update later the review status for some of my entries.

![](./media/IAP159-1.png)

If I chose "display all reviewed entries", I can update anytime some of the entries decision and chose to "sign off" later.

![](./media/IAP159-2.png)

If I chose "sign off", all my decisions will be ready for remediation and I'm not able to change my mind anymore until the _review owner_ "Force Bulk Reset" for some or all of my reviewed entries.

![](./media/IAP159-3.png)

I can close my web browser. Depending on the configuration chosen, the "signed-off" entries will automatically go in a "pending remediation" state within the next days or manually by the _review owner_.  
Then the _technical owner_ or _review owner_ will have the ability to process and monitor the remediation from the remediation management user interface.

![](./media/IAP159-4.png)

### Grouped list mode review

To facilitate the review, _reviewers_ can group entries by account login, identity name, permission or application. This mode allows bulk approval or bulk revocation.

Grouped by permission:

![](./media/IAP170.png)

Grouped by application:

![](./media/IAP171.png)

### Pivot table mode review

This mode is a graphic mode and allows _reviewers_ to have graphic view.

All entries can be organized to have a rapid view and help to identify discrepancies between accounts. This option allows cluster sorting of crosstable cells using an **advanced classification algorithm**. This will help the end-user to work on peer group. To activate it, he needs to click on the icon on the upper left (framed in red in the copyscreen below). In the case of a cross-table listing identities, accounts and their related permissions, when clicking on the "clustering" button in the cross-table, the data is sorted to group users by similar permission sets. Biggest blocks are displayed to the top left of the cross-table, making easier to tackle the most significant groups of similar entries and to identify the outliers at the right and bottom.

Discrepancy accounts will be quickly identified as well. With this mode bulk approval and bulk revocation are interesting.

![](./media/IAP172.png)

Filters on the pivot table can be directly applied to facilitate review.

![](./media/IAP173.png)

### Reviewing entries and delegate some entries to review to my team

Noel HOGAN receives a gentle reminder, he connects to the RadiantOne Identity Analytics interface to do the review.  
He wants to delegate the review of all the "Elyxo" entries to a member of his team, responsible for this application.

He filters the list to show only entries related to elyxo

![](./media/IAP165-1.png)

and he selects all entries thanks to the _Check all_ option

![](./media/IAP165-2.png)

and select _Ask team for help..._

![](./media/IAP165.png)

Noel can now pick a team member to delegate those entries.

![](./media/IAP165-3.png)

The following delegation principles are applied:

- When an individual reviews an entry as a _line manager_ of the account owner, he can only delegate this entry to a team member
- When an individual reviews an entry as an _application business owner_, he can only delegate this entry to the other application business owners
- When you want to delegate several entries at once, the list **must** be uniform (you cannot delegate at the same time _line managers_ entries and _application owners_ entries)
- When you are the _default reviewer_ of an entry, you cannot delegate it
- You cannot delegate the review of an entry in a way that one will have to review himself

When Noel clicks on "Check", if the person cannot be the _reviewer_, the solution gives him the reason in a window:

![](./media/IAP166.png)

In case of doubt, you can display the 'Reviewer origin' column in the table.

Noel selects Philip TORRES in the list:

![](./media/IAP167.png)  
![](./media/IAP168.png)

Once done, the entries are now assigned to Philip. However, if he changed his mind, he still can display the related entries by unchecking the option "Hide entries delegated to team members". He can also add columns, like the "Reviewer name", to manage entries if he has different delegatees, by clicking on the "..." on the right and selecting "Configure columns".

![](./media/IAP168-1.png)

Then he still can select them and reset them in order to delegate them to another person.

![](./media/IAP168-2.png)

> From a review campaign management perspective we keep track of all the delegations by enforcing the RACI principles.  
> The initial _reviewers_ are considered as **accountable** while the delegated _reviewers_ are considered as **responsible**.  
> This can be highlighted in the review campaign management interface.

![](./media/IAP169.png)

As you can notice, a small icon appears at the beginning of the line because this review has been self-delegated. You can further display the *'*accountable name\* if you want to have both the **responsible** and the **accountable** information.

If needed you can reset the delegation status by selecting those entries and clicking on _Force bulk reset_

![](./media/IAP174.png)

## Step 9 - Managing pending signed-off entries

During the campaign, you can reach the review follow-up interface to manage the the entries signed off so far and start remediation.

When entries are in that particular state, it means that the _reviewer_ cannot change his decision anymore. These entries are ready to be remediated. The remediation can be launched automatically based on the script that is executed daily and manually by the _review owner_.  
By selecting entries and clicking on "Proceed Now", the "signed off" entries will be immediately set in "pending remediation" state.  
By selecting entries and clicking on "Force Bulk Reset", the entries will once again be available to the _reviewer_ so that he can change his decisions.

![](./media/IAP164.png)

> 1. The "proceed now" option is also hidden by default. To make it available, it requires to set the `ias_reviewcanproceedsignedentries` variable to `true`.
> 2. To automate the change from "signed off" to "pending remediation", the variable `ias_reviewautomateproceedsignedentries` and `ias_reviewproceedsignedentriesdelay` have to be set to in the configuration of the project. When `ias_reviewautomateproceedsignedentries` is set to `true` and `ias_reviewproceedsignedentriesdelay` is set to a number of days, the entries will automatically go from a "Signed-off" state to a "Proceed: Remediation Pending" state after the number of days indicated. The remediation will then have to be launched and managed through the "Remediation Management" page. To allow this automation, the related workflow (`bwaccess360_automateProceedSignofAccessRights`) needs to be launch using a batch.

## Step 10 - Finalizing the review campaign

The review campaign is now almost done, only some entries still need to be reviewed.

![](./media/IAP175.png)

Miguel MORENO has not reviewed any entries, he still have 63 entries to review.  
Antoinette GONZALES has reviewed all her entries, but she has not signed off.

Regarding Miguel MORENO, after a quick call with him, the _review owner_ decides to approve the 63 entries and make the signed off.
In order to do so, he switch to the _Entries to review_ tab, filter on the Reviewer "Miguel MORENO", right click on the table to select all entries and force those entries status to Approval.

![](./media/IAP176.png)

As you can see, once forced as _approved_, those entries have been marked as reviewed as _Jaime ROBERTSON_ (the _review owner_) on behalf of _Miguel MORENO_. It means that when you force a review status as an administrator, RadiantOne Identity Analytics considers that you are acting **on behalf of** the accountable _reviewer_.

![](./media/IAP177.png)

All entries have now been reviewed, but the "sign off" as not been done by Miguel and Antoinette. As asked by Miguel, I can directly as the _review owner_ force the "sign off" so that we can immediately proceed with the remediation phase.

![](./media/IAP177-bis.png)

Now that all entries have been signed off, let's go back to the _Access Review Management_ page and finalize it:
Select the review campaign and click on _Finalize_.

![](./media/IAP178.png)

In the example above, some entries still need to be reviewed. This is why a warning message appears and a decision regarding those entries must be taken:

- mark those remaining entries as to be _revoked_
- mark those remaining entries as _ok_
- mark those remaining entries as _not reviewed_

> [!warning]
>
> SQL server database limitation: when using a SQL Server database (on-premise installation, self-managed k8s and SaaS are not concerned here), you cannot revoke more than 2000 entries at the “Finalize exam” stage. In that case, _not reviewed_ has to be selected.

In our case we will mark them as _not reviewed_ even though we **know** that it will correspond to a review failure, and add a comment to:

![](./media/IAP178-bis.png)

> Once finalized a review cannot be updated anymore wether the automate remediation is activated or not. In any case, the remediation will be automatically launched once the review campaign is finalized. This background operation can take some time.

The review is now finalized, a compliance report is automatically generated and can be downloaded through the _Access Review Management_ interface. To do so, click on your campaign in the list and then on the right side click on the download button. If you have several review instances, you can also download directly in the review history section the related compliance report by clicking on the icon framed in red in the screenshot below:

![](./media/IAP181.png)

![](./media/IAP180.png)

You can also browse the review campaign follow-up dashboard by clicking on the **Details** button to access the KPIs:

![](./media/IAP183.png)

> _Review status_ and _Actions Requested_ link to _accounts_ and _permissions_ objects in the Identity Ledger, therefore if data is refreshed and those objects disappear they won't be listed anymore. As a result consider the compliance report as the **only** source of trust to prove that your review perimeter has been done.

You can also reach the "Compliance Report" tab to view, filter and browse through the reviewed entries and download on the upper right the PDF report. You can display the results in te table grouped by reviewer by checking the related option:

![](./media/IAP183-bis.png)

You need to uncheck the option "Groups result by reviewer" to export the data in an excel spreadsheet:

![](./media/IAP183-ter.png)

## Step 11 - Following up the remediation

Once your review campaign is finalized, or once a _reviewer_ has signed off his review if you activated the immediate remediation, requested remediations are automatically triggered.

You can follow up the remediation progress through the menu entry _Remediation management_.

> To automate the change from "signed off" to "pending remediation", the variable `ias_reviewautomateproceedsignedentries` and `ias_reviewproceedsignedentriesdelay` have to be set to in the configuration of the project. When `ias_reviewautomateproceedsignedentries` is set to `true` and `ias_reviewproceedsignedentriesdelay` is set to a number of days, the entries will automatically go from a "Signed-off" state to a "Proceed: Remediation Pending" state after the number of days indicated. The remediation will then have to be launched and managed through the "Remediation Management" page. To allow this automation, the related workflow (`bwaccess360_automateProceedSignofAccessRights`) needs to be launch using a batch.

By default, it gives you a consolidated overview of _all_ the remediation, whatever the review campaigns.

Each remediation is associated with the corresponding **application technical owners**.
While remediation are in progress, application technical owners will see those remediation in their interface.

A remediation is following a simple ITSM change management process. Each remediation has its own current status and open/close state.

![](./media/image46.png)

> When the resource on which a remediation is launched is no longer available in the current timeslot (the data relating to the resource has not been loaded), the entries will remain in "pending" status. In this case, the remediation administrator must force the status to "won't fix".

In our use case, once the _remediation management_ displayed, the administrator can follow up the remediation
We can notice that some action have already been made

![](./media/image47.png)

![](./media/IAP184.png)

We can filter the remediation UI for our review campaign thanks to the _Advanced Filters_ feature in the _Details_ toolbar as for now we only want to follow up remediation progress related to our review campaign

![](./media/IAP185.png)

We click on _Send a message_ in order to send a mail to **all** the application technical owners with pending remediation

![](./media/image50.png)

![](./media/image51.png)

## Step 12 - Revoke entries as an application technical owner

As a technical SAP application owner, Kimberly receives an email.
She connects to the Identity Analytics platform to access the pending remediation list.

![](./media/IAP186.png)

She revokes all the access in SAP except the one for `MARTEAU13` as this one is still needed

![](./media/IAP187.png)

## Step 13 - Double-check that all remediation have **really** been done

Once remediation are marked as done in the Identity Analytics platform, the RadiantOne Identity Analytics administrator refresh the data by extracting and loading fresh data from the target systems (HR, SAGE and Elyxo)

The Identity Analytics administrator can double-check in _Remediation Management_ if everything is ok.
In our case, although Kimberly has marked the remediation as been done, nothing has been done in SAP: The access rights are still active

This is automatically highlighted in the _Remediation Management_: A new section _discrepancies_ appears and list all those problems

![](./media/IAP188.png)

The Identity Analytics administrator now have to investigate with the application owner why we ended up with this situation
