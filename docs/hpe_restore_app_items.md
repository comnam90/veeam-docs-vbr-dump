---
title: "Performing Application Item Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_restore_app_items.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Application Item Restore


With application item restore, you can use backups to restore the following data:

* Microsoft Active Directory objects and containers
* Microsoft Exchange mailboxes, folders and messages
* Microsoft SharePoint sites and lists
* Microsoft SQL Server
* Oracle databases

To restore application items from a VM backup, do the following:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, expand the necessary backup job, right-click the VM that contains an application you want to restore, select Restore application items and select the application.

Alternatively, expand the necessary backup job, select the VM, click Application Items on the ribbon and select the application.

1. In the restore wizard, select a restore point that will be used to restore the application, specify a restore reason and click Browse.
2. Use the [Veeam Explorers application](restore_veeam_explorers.md) to proceed with the restore operation.

|  |
| --- |
| Tip |
| As an alternative to application item restore, you can also [perform file-level restore](hpe_vm_guest_restore.md) to recover standalone databases. |

[![Performing Application Item Restore](images/hpe_restore_app_items.webp)](images/hpe_restore_app_items.webp "Performing Application Item Restore")

Page updated 2026-07-22

