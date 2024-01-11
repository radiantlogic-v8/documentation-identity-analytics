---
title: "Identity Analytics Integration Guide"
description : "Identity Analytics Integration Guide"
---

# Available Metadata

Metadata are automatically computed in order to facilitate the analysis and to provide metrics and trends regarding the entities.

Metadatas are provided as a series of "extended attributes" of the entities.

As those metadata are part of the datamodel you can use them in the user interfaces (such as search pages) or in your custom reports or analytics.

> [!warning] If you plan to use those metadatas in your custom views, you **MUST** only use the `bwa_XXXanalytics` metadatas, the other ones are 'transient' metadatas used only during the execution plan, RadiantOne Identity Analytics won't enforce compatibility on those transient metadatas among product versions and RadiantOne Identity Analytics reserves the right to remove those transient metadatas in a later product version.

![](./media/image42.png)

Here is a summary of the available metadatas:  

---

- **Attribute Name:** `nbdirectmembers`
- **Description:** nb direct identity
- **Entity:** Organisation

---

- **Attribute Name:** `nbtotalmembers`
- **Description:** nb total identity
- **Entity:** Organisation

---

- **Attribute Name:** `nbrisks`
- **Description:** nb problems
- **Entity:** Account, Identity

---

- **Attribute Name:** `maxrisklevel`
- **Description:** max risk level
- **Entity:** Account, Identity

---

- **Attribute Name:** `riskscore`
- **Description:** risk score
- **Entity:** Account, Identity, Organisation

---

- **Attribute Name:** `riskrank`
- **Description:** risk rank
- **Entity:** Account, Identity, Organisation

---

- **Attribute Name:** `aggnbrisks`
- **Description:** aggregated nb problems
- **Entity:** Identity

---

- **Attribute Name:** `aggmaxrisklevel`
- **Description:** aggregated max risk level
- **Entity:** Identity, Organisation

---

- **Attribute Name:** `aggriskscore`
- **Description:** aggregated risk score
- **Entity:** Identity, Organisation

---

- **Attribute Name:** `aggriskrank`
- **Description:** aggregated risk rank
- **Entity:** Identity

---

- **Attribute Name:** `nbgroup`
- **Description:** nb groups
- **Entity:** Identity, Repository

---

- **Attribute Name:** `nbdirectgroup`
- **Description:** nb direct groups
- **Entity:** Identity

---

- **Attribute Name:** `nbaccount`
- **Description:** nb active accounts
- **Entity:**  Permission, Application, Group, Repository

---

- **Attribute Name:** `nbidentity`
- **Description:** nb identities with active accounts
- **Entity:**  Permission, Application, Group, Repository

---

- **Attribute Name:** `nbdirectaccount`
- **Description:** nb direct active accounts
- **Entity:**  Group

---

- **Attribute Name:** `nbdirectidentity`
- **Description:** nb identities with active direct accounts
- **Entity:**  Group

---

- **Attribute Name:** `nbdirectaccountright`
- **Description:** nb direct rights with active accounts
- **Entity:**  Application, Repository

---

- **Attribute Name:** `nbdirectidentityright`
- **Description:** nb direct rights with identities with active accounts
- **Entity:**  Application, Repository

---

- **Attribute Name:** `nbidentityrisks`
- **Description:** nb identities with risks
- **Entity:**  Organisation

---

- **Attribute Name:** `nbidentityrisksratio`
- **Description:** nb identities with risks as a percentage
- **Entity:**  Organisation

---

- **Attribute Name:** `nbdirectrole`
- **Description:** nb direct permission of type role per application
- **Entity:** Account

---

- **Attribute Name:** `nbbusinessactivity`
- **Description:** nb business activity
- **Entity:** Account, Identity, Organisation,  Application

---

- **Attribute Name:** `nbprofile`
- **Description:** nb profile
- **Entity:**  Application

---

- **Attribute Name:** `nbpermission`
- **Description:** nb permission
- **Entity:**  Application

---

- **Attribute Name:** `nbsubpermission`
- **Description:** nb sub permissions
- **Entity:**  Permission

---

- **Attribute Name:** `nbtheoretical`
- **Description:** nb theoretical rights
- **Entity:** Account, Identity, Organisation, Permission, Application

---

- **Attribute Name:** `nbdirectright`
- **Description:** nb rights (total)
- **Entity:** Account

---

- **Attribute Name:** `nbright`
- **Description:** nb direct rights
- **Entity:** Account

---

- **Attribute Name:** `nbapplication`
- **Description:** nb applications (Profile)
- **Entity:** Identity, Organisation  Group, Repository

---

- **Attribute Name:** `nshare`
- **Description:** nbshare (Filesystem)
- **Entity:** Identity, Organisation  Group, Repository

---

- **Attribute Name:** `isroot`
- **Description:** is business activity a root business activity
- **Entity:**  Permission

---

- **Attribute Name:** `nbperimeter`
- **Description:** nb perimeters used in the application
- **Entity:** Account, Identity, Organisation,  Application

---

- **Attribute Name:** `nbdirectsuborg`
- **Description:** nb of direct sub-organisations
- **Entity:**  Organisation

---

- **Attribute Name:** `nbsuborg`
- **Description:** nb of sub-organisations (direct+indirect)
- **Entity:**  Organisation

---

- **Attribute Name:** `depth`
- **Description:** depth level
- **Entity:**  Organisation

---

- **Attribute Name:** `nbusage`
- **Description:** nb of usages found
- **Entity:** Account, Identity,  Permission, Application, Repository

---

- **Attribute Name:** `nbreadaccess`
- **Description:** nb read access
- **Entity:**  Permission, Application

---

- **Attribute Name:** `nbwriteaccess`
- **Description:** nb write access
- **Entity:**  Permission, Application

---

- **Attribute Name:** `nbfullcontrolaccess`
- **Description:** nb full controll access
- **Entity:**  Permission, Application

---

- **Attribute Name:** `nbfolder`
- **Description:** nb folder
- **Entity:**  Application

---

- **Attribute Name:** `nbmanagedfolder`
- **Description:** nb managed folder
- **Entity:**  Application

---

- **Attribute Name:** `joborg`
- **Description:** jobs and organisations (aggregated string)
- **Entity:** Identity

---

- **Attribute Name:** `orgpath`
- **Description:** organisation path (aggregated org shortname)
- **Entity:** Identity

---
