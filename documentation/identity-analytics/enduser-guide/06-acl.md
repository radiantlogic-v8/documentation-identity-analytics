---
title: "Identity Analytics Enduser Guide"
description : "Identity Analytics Enduser Guide"
---

# ACLs definitions  

The access rights to share and shared folders are displayed in IAS/IAP interfaces as Access Control Lists (ACLs). There are three different ways to display them:

- simplified ACLs, for a quick and easy understanding, especially for business end-users,
- basic ACLs, for a mapping to the Microsoft Windows permissions that are set in the Windows GUI,
- advanced ACLs, for expert end-users.

In most of the tables, the simplified ACLs are used. When using the Share and Folders details pages or windows, the end-user has the possibility to check basic ACLs and to display them as advanced ACLs if needed.  

Here is the definition of each ACLs display options:

- simplified ACLs:

| **Simplified ACLs**     | **Simplified ACLs label**    |
| :---------------------: | :--------------------------- |
| R                       | Read                         |
| W                       | Write (Windows)              |
| C                       | Total Control                |

- basic ACLs:

| **Basic ACLs**                | **Basic ACLs label**          | **Advanced ACLs corresponding**               |
| :---------------------------: | :---------------------------- | :-------------------------------------------- |
| R                             | Read (Windows)                | RGFE                                          |
| W                             | Write (Windows)               | WGAML                                         |
| X                             | Read and Execute/             | RXGFE                                         |
| X                             | List Folder Content (Windows) | RXGFE                                         |
| M                             | Modify (Windows)              | RWXGAFEMDL                                    |
| F                             | Full Control (Windows)        | RWXGASPFEMDL                                  |
| S                             | Special (Windows)             | any combination not matching any of the above |
| L                             | Read (Identity Analytics)     | R                                             |
| U                             | Update (Identity Analytics)   | WAMLDS                                        |
| C                             | Control (Identity Analytics)  | PO                                            |

- advanced ACLs:

| **Advanced ACLs** | **Advanced ACLs label**         | **Advanced ACLs description**                                                                                      |
| :---------------: | :------------------------------ | :----------------------------------------------------------------------------------------------------------------- |
| R                 | List folder or Read File        | Data can be read from the file or folder can be listed                                                             |
| W                 | Create Files or Write Data      | Data can be written to the file or files created inside the folder                                                 |
| X                 | Traverse Folder or Execute File | Data can be read into memory from the file using system paging I/O                                                 |
| G                 | Read Permissions                | The access control list and ownership associated with the file can be read                                         |
| A                 | Create Folders or Append Data   | Data can be appended to the file or subfolders can be added to the folder                                          |
| S                 | Delete Subfolders and Files     | File and empty folders can be deleted in this shared folder even without having right access to that shared folder |
| P                 | Change Permissions              | The access control list and ownership associated with the file can be written                                      |
| F                 | Read Extended Attributes        | Extended attributes associated with the file can be read                                                           |
| O                 | Take ownership                  | Ownership information associated with the file can be written                                                      |
| E                 | Read Attributes                 | Attributes associated with the file can be read                                                                    |
| M                 | Write Extended Attributes       | Extended attributes associated with the file can be written                                                        |
| D                 | Delete                          | The file can be deleted                                                                                            |
| L                 | Write Attributes                | Attributes associated with the file can be written                                                                 |
