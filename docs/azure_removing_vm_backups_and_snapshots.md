---
title: "Removing VM Backups and Snapshots"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_removing_vm_backups_and_snapshots.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing VM Backups and Snapshots


The backup appliance applies the [configured retention policy settings](azure_vm_backup_policy_schedule.md) to automatically remove cloud-native snapshots and image-level backups created for Azure VMs by backup policies. If necessary, you can also remove the backed-up data manually.

|  |
| --- |
| Important |
| Do not delete backups from Microsoft Azure storage accounts in the Microsoft Azure portal. If some backup in a backup chain is missing, you will not be able to roll back Azure VM data to the necessary state. |

To remove backed-up data manually, do the following:

1. Navigate to Protected Data > Virtual Machines.
2. Select Azure VMs whose data you want to remove.
3. Click Remove and select either of the following options:

* Snapshots > All — to remove all cloud-native snapshots created for the selected Azure VMs both by backup policies and manually.
* Snapshots > Local — to remove all cloud-native snapshots created for the selected Azure VMs by backup policies.
* Snapshots > Manual — to remove all cloud-native snapshots created for the selected Azure VMs manually.
* Backups > All — to remove all image-level backups created for the selected Azure VMs.
* Backups > Backup — to remove all image-level backups created in repositories for the selected Azure VMs.
* Backups > Archive — to remove all image-level backups created in archive repositories for the selected Azure VMs.
* Snapshots and Backups — to remove both cloud-native snapshots and image-level backups created for the selected Azure VMs.

[![Removing Backups and Snapshots](images/azure_remove_backups_vm.webp)](images/azure_remove_backups_vm.webp "Removing Backups and Snapshots")

Page updated 2026-07-01

