---
title: "Performing Entire VM Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_entire_vm_restore_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Entire VM Restore


In case a disaster strikes, you can restore entire Azure VM from a cloud-native snapshot or an image-level backup. Veeam Backup & Replication allows you to restore one or more Azure VMs at a time, to the original location or to a new location.

How Instance Restore Works

To restore Azure VMs from cloud-native snapshots, Veeam Backup & Replication uses [native Azure capabilities](https://learn.microsoft.com/en-us/azure/virtual-machines/snapshot-copy-managed-disk?tabs=portal). To restore VMs from image-level backups, Veeam Backup & Replication uses different algorithms depending on whether a backup appliance is added to the backup infrastructure:

* If a backup appliance is connected to the backup server, Veeam Backup & Replication uses the restore algorithm described in section [Performing Entire VM Restore](azure_entire_vm_restore_ui.md).
* If a backup appliance is not connected to the backup server, Veeam Backup & Replication uses the restore algorithm described in [How Restore to Microsoft Azure Works](restore_azure_hiw.md).

How to Perform VM Restore

To restore an entire VM, do the following:

1. [Launch the Restore to Azure wizard](azure_vm_restore_console_wizard.md).
2. [Select a restore point](azure_vm_restore_console_point.md).
3. [Choose a restore mode](azure_vm_restore_console_mode.md).
4. [Specify an Azure subscription and region](azure_vm_restore_console_subscription.md).
5. [Specify a new VM name and resource group](azure_vm_restore_console_name.md).
6. [Specify VM configuration settings](azure_vm_restore_console_zone.md).
7. [Specify a VM size](azure_vm_restore_console_size.md).
8. [Configure network and security group settings](azure_vm_restore_console_network.md).
9. [Specify a restore reason](azure_vm_restore_console_reason.md).
10. [Finish working with the wizard](azure_vm_restore_console_finish.md).

Page updated 2026-06-26

