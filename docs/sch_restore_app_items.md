---
title: "Performing Application Item Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_restore_app_items.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Performing Application Item Restore


With application item restore, you can use Scale Computing HyperCore backups to restore the following data:

* Microsoft Active Directory objects and containers
* Microsoft Exchange mailboxes, folders and messages
* Microsoft SharePoint sites and lists
* Microsoft SQL Server
* Oracle databases

|  |
| --- |
| Note |
| Due to technical limitations, Veeam Plug-in for Scale Computing HyperCore produces only crash-consistent (not application-consistent) backups that in some cases cannot be used for application item restore. |

To restore application items from a VM backup, do the following:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, expand the necessary backup job, select the VM that contains an application you want to restore.
4. Click Application Items on the ribbon and select the application.

Alternatively you can right-click the VM, select Restore application items and select the application.

1. In the restore wizard, select a restore point that will be used to restore the application, specify a restore reason and click Browse.
2. In the Veeam Explorer application, perform the steps described in the [Veeam Explorers User Guide](https://helpcenter.veeam.com/docs/vbr/explorers/explorers_introduction.html?ver=13).

|  |
| --- |
| Tip |
| As an alternative to application item restore, you can also [perform file-level restore](sch_vm_guest_restore.md) to recover standalone databases using Veeam Explorers. |

[![Performing Application Item Restore](images/sch_restore_app_items.webp)](images/sch_restore_app_items.webp "Performing Application Item Restore")


