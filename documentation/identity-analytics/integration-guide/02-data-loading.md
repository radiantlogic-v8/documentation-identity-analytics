---
title: "Identity Analytics Integration Guide"
description : "Identity Analytics Integration Guide"
---

# Data loading

In order to benefit from IAP data must be properly loaded into the Identity Ledger. The following rules must be followed:

## Identity

Identities are loaded as usual.

As a best practice, you should perform a first data loading with all users (both current and former users) in order for RadiantOne Identity Analytics to have a global view of both who is working for the company and who has been working for the company. It will help the solution to reconcile and spot leaver accounts.

If it is not necessary, it is recommended to load only "active identities" on subsequent timeslots. An alternative could be to load both active identities & inactive identities who left less than 12 months ago.

As a general rule, inactive identities are not displayed in IAP **unless** they still have active accounts.  

## Organisation

Organisations are loaded as usual. Although it is not recommended, you can assign several organisations to an identity.  

## Line manager

A new management link is available starting with Braille: `Management of Identity`  

Through this link you can dynamically load, compute, manually assign who is the line manager of whom.

Like any other management links, an `expertise domain` is available with the link. As a result you can assign several managers to an identity with different `expertise domain`.  

The best practice is to load HR management information in Identity & Organisation objects (such as operational manager link and organisation manager link) and to configure the line manager link based on the most relevant information.

This means that at the end of the day, the line manager link is no longer read only information based the HR datasources but dynamic information that can be computed based on the HR datasources: You can manually update it later on from the web portal if needed.

As a best practice, you should also rely on this new link for your Access Certification campaigns as it is much more flexible (you can manage data quality issues from the web portal directly)

This link is the one displayed in IAP every time you have "line manager" information displayed.  

## Resource manager

You should load resource management information whenever possible, this information could be for instance available in a CMDB system.

When loading management information, you **MUST** configure the `expertise domain` with one of the following value:

- `businessowner` for people identified as business owner (typically the ones accountable for access certification) 
- `technicalowner` for technical owner (typically the ones accountable for target system updates)

## Repository

Repositories are loaded as usual.

If you are loading several instances of the same repository type, you **SHOULD** fulfill the repositoryfamily attribute.
The repositoryfamily attribute can be used in search pages as well as to override reports & analytics (see advanced section)

## Account

Accounts are loaded as usual.  

Please note that disabled accounts are not displayed in IAP, except in repository details. If the disabled attribute is not fulfilled, the account is considered active.

## Application

You can load applications as usual. All applications must be identified with `applicationtype=Profile`  

If you are loading several instances of a same system, it is a best practice to identify the system through the `applicationfamily` attribute. or instance, if you are loading several SAP systems, you should have `applicationfamily=SAP`
The `applicationfamily` attribute can be used in search pages as well as to override reports & analytics (see advanced section)

## Permission

You can load permissions as usual.

Please note that on most IAP user interfaces, only coarse grain permissions are displayed. Coarse grain permissions are identified through `permissiontype=Role`, as a result you **MUST** configure `permissiontype=Role` if you want the permissions displayed in IAP.

Please note that most IAP interfaces are only displaying direct account/permission associations (either direct or through groups) as it considers that sub-permissions are not directly assigned to the account but rather "inherited" from the main permission.

For fine grain permission, the best practice is to fulfill permissiontype with a relevant information, for instance `permissiontype=Transaction`, `permissiontype=AuthObj`, ... as permission type can also be used in search pages as well as to override reports & analytics (see advanced section)

## Business Activity

Business activities are the preferred way to perform SoD checks.
As a result, if you want to configure SoD check, you **MUST** load business activities.
Business activities are loaded as "permission" objects, you **MUST** identify them with `permissiontype=Activity`  

## SoD matrix

Even though, the former activity/sub-activity way of describing SoD checks is still supported, you should consider it as deprecated and you **SHOULD** load SoD checks through basic expressions.

Please refer to the product documentation on how to write down SoD rules by leveraging the expression language.
[https://documentation.brainwavegrc.com](https://documentation.brainwavegrc.com)

## Theoretical rights

Theoretical rights are natively supported in IAP, you just have to load them and to configure them.

## Active Directory

You **MUST** use the latest Active Directory add-on to extract and load active directory data as IAP rely on specific attributes to display the content in a proper way (such as repositoryfamily)

## Unstructured Data

You **MUST** use the latest Unstructured Data add-on to extract and load Unstructured Data data as IAP rely on specific attributes to display the content in a proper way (such as repositoryfamily)
