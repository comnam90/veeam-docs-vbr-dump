---
title: "Step 3. Select Restore Mode"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/entire_vm_restore_hv_restoremode.html"
last_updated: "9/4/2025"
product_version: "13.0.1.1071"
---


In this article

At the Restore mode step, specify a destination for VM recovery and select whether you want to recover VM tags.

When you perform entire VM restore using Veeam Backup Enterprise Manager, Veeam Backup & Replication automatically selects a backup proxy over which VM data must be transported to the source datastore. You can select a backup proxy manually from the Entire VM Restore wizard in the Veeam Backup & Replication console. For more information, see the [Select Restore Mode](https://helpcenter.veeam.com/docs/vbr/userguide/full_restore_mode_hv.html?ver=13) section of the Veeam Backup & Replication User Guide.

1. Select a restore mode:

* Restore to the original location — select this option to restore the VM with initial settings and to the original location. If this option is selected, you will pass directly to the [Summary](entire_vm_restore_hv_datastore.md) step of the wizard.

During restore to the original location, Veeam Backup & Replication restores only those disks that are included in the backup file. This means that after the restore finishes, you do not have to update existing jobs which process the original VMs.

* Restore to a new location or with different settings — select this option to restore the VM to a new location, or to any location but with different settings. If this option is selected, the Entire VM Restore wizard will include additional steps for customizing VM settings.

During restore to a new location, Veeam Backup & Replication creates new VMs. If you want to process the restored VMs, you must edit existing jobs or create new jobs to process the restored VMs. If you restore VMs with the same name and to the same folder as the original VMs, Veeam Backup & Replication deletes the original VMs. In this case, you must edit existing jobs to exclude original VMs from them.

|  |
| --- |
| Note |
| If you need to run an executable script for the VM before restoring it to the production environment, you can use the Veeam Backup & Replication console to perform entire VM restore in the Staged restore mode. For more information, see the [Select Restore Mode](https://helpcenter.veeam.com/docs/vbr/userguide/full_restore_mode_hv.html?ver=13) section of the Veeam Backup & Replication User Guide. |

1. [For VM restore to the original location] Select the Quick rollback check box to perform incremental restore for the VM. Veeam Backup & Replication will query Changed Block Tracking to get data blocks that are required to revert the VM to the restore point, and will restore only these data blocks. Quick rollback significantly reduces the restore time and has little impact on the production environment.

Enable this option if you restore a VM after a problem that occurred at the level of the VM guest OS: for example, there has been an application error or a user has accidentally deleted a file on the VM guest OS. Do not enable this option if the problem has occurred at the VM hardware level, storage level or due to a power loss.

For more information on quick rollback, its requirements and limitations, see the [Quick Rollback](https://helpcenter.veeam.com/docs/vbr/userguide/incremental_restore.html?ver=13) section of the Veeam Backup & Replication User Guide.

![Step 3. Select Restore Mode](images/entire_vm_restore_hv_restore_mode.webp "Selecting Restore Mode")

Page updated 9/4/2025

Page content applies to build 13.0.1.1071
