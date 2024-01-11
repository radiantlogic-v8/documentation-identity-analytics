---
title: "Identity Analytics Access Review Guide"
description : "Identity Analytics Access Review Guide"
---

# Review Campaign Examples

This chapter presents review campaign configuration examples to cover the most common use cases.  

## Review all access rights for some applications  

This is the most common use case, in order to do so, you have to select the applications that you want to include in your access review campaign.  
You can do it one application by one application:  

![](./media/IAP142.png)  

Or you can do it by using tags:  

![](./media/IAP143.png)  

The default configuration will review **all** active accounts direct access rights (limited to permission type 'Role')  

The reviewer is either a **direct line manager** or an **application owner**.  
Each "user account" will be reviewed by the account owner direct line manager.  
All the other accounts (technical accounts, orphan accounts, ...) will be reviewed by the application owner.  

## Review all user accounts access rights per line manager  

You can restrict your access review to user accounts only if you want to focus on *business line managers* as reviewers.  
In order to do so you just have to select *user accounts* in the *Advanced Mode* section of the configuration page:  

![](./media/IAP144-bis.png)  

## Review Finance department access rights per line manager  

It can be useful to restrict your access review to a given organisation, especially in large organisation.  
Let's say for instance that you want to review SOX applications access rights in the *Finance Department*.  

In order to do so, you will have first to tag all accounts belonging to people working for the *finance departement*.  
  
> You can do it by performing an account search followed by a bulk tagging operation.  

![](./media/IAP203.png)  
  
![](./media/IAP203-bis.png)  
Once done, you will have to select the account tag in the campaign configuration page.

![](./media/IAP202.png)

## Review access rights of people who moved from one organisation to another

This use case is very similar to the previous one, you first have to tag the accounts you want to review with a search:  

![](./media/image91.png)

Once done, you will have to select the account tag in the campaign configuration page.  

## Review technical accounts access rights per application owner  

In order to review technical accounts only, you just have to uncheck *Include User Accounts* in campaign configuration in the *Advanced Mode* section:  

![](./media/IAP204.png)

> *Leavers* account correspond to active accounts belonging to people who are no longer part of the company.  

## Review sensitive access rights per application owner  

In order to review sensitive access rights you first have to tag your sensitive permissions  

![](./media/IAP206.png)  

Once this is done, you configure your access right campaign by  

- Selecting the tag in the *Permissions Review Perimeter*

![](./media/IAP205.png)  

- Force the application owner to review everything in the next step *2. Define Review Strategy*:

![](./media/IAP205-bis.png)  

## Self review of all dormant (unused) user accounts by the users themselves  

In the next step *2. Define Review Strategy*, you can pick *user accounts by themself* if you want the user reviewing themselves. This is very useful to review at-risk users or control defects such as outliers and unused access.  

![](./media/image108.png)  

## Review Only the changes since the last review

In order to review only the changes that occurred since the last review, you have to configure your *Incremental Review Strategy* in the step *2. Define Review Strategy*:

![](./media/IAP207.png)

Keep in mind that an entry will be considered as already been reviewed only if all those conditions are met:

- The entry has been reviewed in the configured time frame (X days)
- For a user account, account owner characteristics have not changed (organisation, job title, internal status)

This will fulfill both the status and the comment columns in your review table. You can also simply remove those entries from the review perimeter by checking "Remove from the list entries who have already been reviewed"

## Review unused accounts access rights

In order to review unused accounts, you will have first to tag them through an account search leveraging a control result

![](./media/IAP208.png)

Once this is done, you configure your access review and select the corresponding tag in *Accounts Review Perimeter*

## Repository accounts review

To launch an repository accounts review, select "Repository accounts Review" in the Access Review Management section. You have to select the repository that you want to include in your accounts review campaign.

![](./media/IAP209.png)  
![](./media/IAP210.png)  

The next steps are the same that application access rights review. Incremental review strategy and reviewers strategy must be defined:  

![](./media/IAP210-bis.png)  

The available *reviewer strategies* are:  

- User accounts by line manager, technical accounts by the repository owner
- User accounts by line manager, all other accounts by the repository owner
- User accounts by themself, all other accounts by the repository owner
- All accounts by the repository owner
- All accounts by the default reviewer

When the accounts review is launch, review is available on "Access 360" section:  

![](./media/IAP211.png)  

Reviewers can start the accounts review. They can approve, revoke or comment one by one, they can also perform bulk operations by selecting several entries at once.  

![](./media/IAP212.png)  

## Repository group membership review

To launch a repository group membership review, select "Repository accounts Review" in the Access Review Management section. You have to select the repository that you want to include in your group review campaign. Note that only group direct members are considered, meaning that an entry is composed of the group, its related repository and the direct account member of the related group.

![](./media/IAP239.png)  
![](./media/IAP240.png)  

The next steps are the same that application access rights review. Incremental review strategy and reviewers strategy must be defined:  

![](./media/IAP240-bis.png)  

The available *reviewer strategies* are:  

- User account members by line manager, technical/service account members by the repository owner
- User account members by line manager, all other members by the repository owner
- User account members by themself, all other members by the repository owner
- User account members by line manager, technical/service account members by the group owner
- User account members by line manager, all other members by the group owner
- User account members by themself, all other members by the group owner
- All members by the group owner
- All members by the repository owner
- All members by the default reviewer

When the group membership review is launch, review is available on "Access 360" section:

![](./media/IAP241.png)  

Reviewers can start the group membership review. They can approve, revoke or comment one by one, they can also perform bulk operations by selecting several entries at once.  

![](./media/IAP242.png)

## Sensitive service accounts by account owners, all other accounts by line manager or repository owner

You can configure more advanced scenarios where you can select who will have to do the review depending on some factors such as risk level, account sensitivity level, last login date, ...
In order to do this you have to enable the `advanced reviewer selection` mode.  

![](./media/IAP229.png)  

Once done, you can define your strategy through a server side javascript.  
This script will be executed for each individual line to review in order to find a valid reviewer. Here is an example.  

![](./media/IAP230.png)

```javascript
// This script identifies the reviewer for each individual review line.

// You have to send back a value amongst the following:
// - linemanager
// - repositoryowner
// - accountowner
// - default
// - myself
// - HRCODE value
// You can also send back a list of values such as linemanager,accountowner,repositoryowner,default
// In this case, the first valid reviewer will be taken (valid = reviewer found + reviewer having an email)
// 
// 
// The following variables are fulfilled for your convenience:
// accountowneruid
// accountownerhrcode
// accountownerfullname
// accountownermail
// linemanageruid
// linemanagerhrcode
// linemanagerfullname
// linemanagermail
// identityuid
// identityhrcode
// identityfullname
// identitymail
// defaultrevieweruid
// defaultreviewerhrcode
// defaultreviewerfullname
// defaultreviewermail
// accountuid
// accountlogin
// repositoryname
// repositoryowneruid
// repositoryownerhrcode
// repositoryownerfullname
// repositoryownermail
// accountmaxrisklevel
// accountsensitivitylevel
// accountnoownercode
// accounttype (user,leave,technical,orphan)
// lastloginindays

if(accounttype.equals('user')) {
  'linemanager,repositoryowner,default';
}
else {
  if(accountsensitivitylevel>2)
    'accountowner,repositoryowner,default';
  else
    'repositoryowner,default';
}
```

> This mode is disabled by default.  The related feature have to be enabled in your project if you want to use advanced review strategies. To do so, you have to edit the following feature file: `\webportal\features\bw_iasreview\iasreview.features`. The feature `ias_accountreviewadvancedreviewermode` for repository accounts reviews and repository group membership reviews has to be associated to the relevant feature sets. Please contact your Identity Analytics project owner to configure this.  

## Sensitive permissions by permission owners, all other permissions by line manager or application owner

You can configure more advanced scenarios where you can select who will have to do the review depending on some factors such as risk level, account sensitivity level, last login date, ...
In order to do this you have to enable the `advanced reviewer selection` mode  

![](./media/IAP231.png)

Once done, you can define your strategy through a server side javascript.
This script will be executed for each individual line to review in order to find a valid reviewer. Here is an example.

![](./media/IAP232.png)

```javascript
// This script identifies the reviewer for each individual review line.

// You have to send back a value amongst the following:
// - linemanager
// - applicationowner
// - accountowner
// - permissionowner
// - default
// - myself
// - HRCODE value
// You can also send back a list of values such as linemanager,permissionowner,applicationowner,default
// In this case, the first valid reviewer will be taken (valid = reviewer found + reviewer having an email)
// 
// 
// The following variables are fulfilled for your convenience:
// applicationowneruid
// applicationownerhrcode
// applicationownerfullname
// applicationownermail
// permissionowneruid
// permissionownerhrcode
// permissionownerfullname
// permissionownermail
// accountowneruid
// accountownerhrcode
// accountownerfullname
// accountownermail
// linemanageruid
// linemanagerhrcode
// linemanagerfullname
// linemanagermail
// identityuid
// identityhrcode
// identityfullname
// identitymail
// defaultrevieweruid
// defaultreviewerhrcode
// defaultreviewerfullname
// defaultreviewermail
// accountuid
// accountlogin
// repositoryname
// accountmaxrisklevel
// accountsensitivitylevel
// accountnoownercode
// permissionuid
// permissioncode
// permissionsensitivitylevel
// applicationuid
// applicationcode
// accounttype (user,leave,technical,orphan)
// lastloginindays

if(accounttype.equals('user')) {
  'linemanager,applicationowner,default';
}
else {
  if(permissionsensitivitylevel>2)
    'permissionowner,applicationowner,default';
  else
    'applicationowner,default';
}

```

> This mode is disabled by default.  The related feature have to be enabled in your project if you want to use advanced review strategies. To do so, you have to edit the following feature file: `\webportal\features\bw_iasreview\iasreview.features`. The feature `ias_rightreviewadvandedreviewermode` for application rights reviews has to be associated to the relevant feature sets. Please contact your Identity Analytics project owner to configure this.  
