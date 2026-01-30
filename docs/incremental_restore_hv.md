---
title: "Quick Rollback"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/incremental_restore_hv.html"
last_updated: "3/24/2025"
product_version: "13.0.1.1071"
---

# Quick Rollback


When you restore a full VM to the original location, you can instruct Veeam Backup & Replication to perform quick rollback — incremental data restore. Instead of restoring an entire VM from a backup file, Veeam Backup & Replication will recover only those data blocks that are necessary to revert the VM to an earlier point in time. Quick rollback significantly reduces the recovery time and has little impact on the production environment.

For quick rollback, Veeam Backup & Replication uses the changed block tracking technology. Veeam Backup & Replication gets information about the current VM state and compares it with the CBT information in the backup file. This way, Veeam Backup & Replication detects what data blocks must be transported back to the production volume to rebuild the VM to the necessary point in time.

It is recommended that you use quick rollback if you restore a VM after a problem that has occurred at the level of the VM guest OS — for example, there has been an application error or a user has accidentally deleted a file on the VM guest OS. Do not use quick rollback if the problem has occurred at the VM hardware level, storage level or due to a power loss.

Considerations and Limitations for Quick Rollback

* To perform quick rollback, make sure that you restore VM to its original location.
* [For Microsoft Hyper-V 2016 and later] You cannot run two restore sessions with quick rollback subsequently. After you restore a VM with quick rollback, the CBT on the original VM is reset. You must run at least one incremental backup job session to be able to perform quick rollback again.
* Quick rollback is not supported if the original VM is replicated using Hyper-V native replication mechanisms.
* Use quick rollback and VM guest OS file exclusion wisely. If you exclude specific files and folders from the VM guest OS during backup and use quick rollback to restore the VM or VM disk from such backup, Veeam Backup & Replication will restore only the content of the backup file. The excluded data will not be restored. For example, if you exclude C:\Folder from the backup, data in this folder will not be backed up and will not be available in the resulting backup file. After some time, data in C:\Folder may change but the folder will still not be backed up (since the job excludes this folder). For this reason, when you perform quick rollback, Veeam Backup & Replication will restore all data that have changed except the excluded C:\Folder.

Related Topics

[Performing Entire VM Restore](performing_full_recovery_hv.md)


