---
title: "Identity Analytics Enduser Guide"
description : "Identity Analytics Enduser Guide"
---

# Computed KPIs  

KPIs are automatically computed during the data loading process, thanks to the "Metadata" technical feature. These KPIs are then distributed in the different search and detail pages, and sometime used in analytics reports also.

## Risk ranking and risk analysis

One of the key features of IAS/IAP is to provide risk assessment and risk ranking to help end-users to identify the most risky situations and mitigate risks.

Three pre-calculated KPIs have been made available at organisation, Identity and Account level:

- the total number of risks
- the maximum risk level
- the risk rank

The combination of these three KPIs will help the end-user to have a good idea of risk level of each resource and allow comparison for a better prioritization. Note that these KPIs are computed during the data upload.  

### Risk Rank  

Risk scoring and risk ranking are based on the control results, it helps in identifying where the problems are located and how the problems evolve. To get the list of all the controls available in your project and used for the Risk calculation, please go to section [How to list all the available controls](./07-customization#advanced-feature-how-to-list-all-the-available-controls-their-description-and-manage-their-execution) of this document.  

Risk scoring is based on an aggregated score of the entity discrepancies, weighted by the controls risk levels.  
Based on the risk scoring, a risk ranking is automatically computed. The higher the worst (account ranked #1 is the MOST RISKY account of the company). Entities with the exact same risk score are ranked the same, this is the reason why the end-user can have ex aequo situations. For more details about how Risk rank is computed, please check out the "Identity Analytics Integration Guide", section: IAS/IAP UX principles > UI Content Principles > Risk scoring & Risk ranking.  

Ranking is very useful to reorder entries with a risk approach perspective. Risks are available both on the search pages and on the details pages.  

### Nb of risks and Max risk level  

The end-user can associate to the risk rank the Nb of risks related to the entity. This helps to understand the context.
As in the example below, the end-user can have more risks but with a lower severity for an entity (Jaime ROBERTSON), so that the risk rank will be higher than for others with more severe controls defects (Sophia FOX).

![](./media/image-80-Search-identities_RiskRank.png)

## Other computed KPIs  

Other KPIs are automatically computed during the load of data in order to facilitate the analysis and to provide metrics and trends regarding the entities. These KPIs are provided as a series of “extended attributes” of the entities. As those KPIs are part of the data model you can use them in the user interfaces (such as search pages) or in your custom reports or analytics.  

Here is a summary of the available computed KPIs:

---

- **Attribute name:** `nbdirectmembers`
- **Description:** Number direct identity
- **Entity:** Organisation

---

- **Attribute name:** `nbtotalmembers`
- **Description:** nb total identity
- **Entity:** Organisation

---

- **Attribute name:** `nbrisks`
- **Description:** nb problems
- **Entity:** Account, Identity

---

- **Attribute name:** `maxrisklevel`
- **Description:** max risk level
- **Entity:** Account, Identity

---

- **Attribute name:** `riskscore`
- **Description:** risk score
- **Entity:** Account, Identity, Organisation

---

- **Attribute name:** `riskrank`
- **Description:** risk rank
- **Entity:** Account, Identity, Organisation

---

- **Attribute name:** `aggnbrisks`
- **Description:** aggregated nb problems
- **Entity:** Identity

---

- **Attribute name:** `aggmaxrisklevel`
- **Description:** aggregated max risk level
- **Entity:** Identity, Organisation

---

- **Attribute name:** `aggriskscore`
- **Description:** aggregated risk score
- **Entity:** Identity, Organisation

---

- **Attribute name:** `aggriskrank`
- **Description:** aggregated risk rank
- **Entity:** Identity

---

- **Attribute name:** `nbgroup`
- **Description:** nb groups
- **Entity:** Identity, Repository

---

- **Attribute name:** `nbdirectgroup`
- **Description:** nb direct groups
- **Entity:** Identity

---

- **Attribute name:** `nbaccount`
- **Description:** nb active accounts
- **Entity:** Permission, Application, Group, Repository

---

- **Attribute name:** `nbidentity`
- **Description:** nb identities with active accounts
- **Entity:** Permission, Application, Group, Repository

---

- **Attribute name:** `nbdirectaccount`
- **Description:** nb direct active accounts
- **Entity:** Group

---

- **Attribute name:** `nbdirectidentity`
- **Description:** nb identities with active direct accounts
- **Entity:** Group

---

- **Attribute name:** `nbdirectaccountright`
- **Description:** nb direct rights with active accounts
- **Entity:** Application, Repository

---

- **Attribute name:** `nbdirectidentityright`
- **Description:** nb direct rights with identities with active accounts
- **Entity:** Application, Repository

---

- **Attribute name:** `nbidentityrisks`
- **Description:** nb identities with risks
- **Entity:** Organisation

---

- **Attribute name:** `nbidentityrisksratio`
- **Description:** nb identities with risks as a percentage
- **Entity:** Organisation

---

- **Attribute name:** `nbdirectrole`
- **Description:** nb direct permission of type role per application
- **Entity:** Account

---

- **Attribute name:** `nbbusinessactivity`
- **Description:** nb business activity
- **Entity:** Account, Identity, Organisation, Application

---

- **Attribute name:** `nbprofile`
- **Description:** nb profile
- **Entity:** Application

---

- **Attribute name:** `nbpermission`
- **Description:** nb permission
- **Entity:** Application

---

- **Attribute name:** `nbsubpermission`
- **Description:** nb sub permissions
- **Entity:** Permission

---

- **Attribute name:** `nbtheoretical`
- **Description:** nb theoretical rights
- **Entity:** Account, Identity, Organisation, Permission, Application

---

- **Attribute name:** `nbdirectright`
- **Description:** nb rights (total)
- **Entity:** Account

---

- **Attribute name:** `nbright`
- **Description:** nb direct rights
- **Entity:** Account

---

- **Attribute name:** `nbapplication`
- **Description:** nb applications (Profile)
- **Entity:** Identity, Organisation, Group, Repository

---

- **Attribute name:** `nshare`
- **Description:** nbshare (Filesystem)
- **Entity:** Identity, Organisation, Group, Repository

---

- **Attribute name:** `isroot`
- **Description:** is business activity a root business activity
- **Entity:** Permission

---

- **Attribute name:** `nbperimeter`
- **Description:** nb perimeters used in the application
- **Entity:** Account, Identity, Organisation, Application

---

- **Attribute name:** `nbdirectsuborg`
- **Description:** nb of direct sub-organisations
- **Entity:** Organisation

---

- **Attribute name:** `nbsuborg`
- **Description:** nb of sub-organisations (direct+indirect)
- **Entity:** Organisation

---

- **Attribute name:** `depth`
- **Description:** depth level
- **Entity:** Organisation

---

- **Attribute name:** `nbusage`
- **Description:** nb of usages found
- **Entity:** Account, Identity, Permission, Application, Repository

---

- **Attribute name:** `nbreadaccess`
- **Description:** nb read access  
- **Entity:** Permission, Application

---

- **Attribute name:** `nbwriteaccess`
- **Description:** nb write access
- **Entity:** Permission, Application

---

- **Attribute name:** `nbfullcontrolaccess`
- **Description:** nb full controll access
- **Entity:**  Permission, Application

---

- **Attribute name:** `nbfolder`
- **Description:** nb folder
- **Entity:** Application

---

- **Attribute name:** `nbmanagedfolder`
- **Description:** nb managed folder
- **Entity:** Application

---

- **Attribute name:** `joborg`
- **Description:** jobs and organisations (aggregated string)
- **Entity:** Identity

---

- **Attribute name:** `orgpath`
- **Description:** organisation path (aggregated org shortname)
- **Entity:** Identity

---
