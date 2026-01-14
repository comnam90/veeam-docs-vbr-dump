---
title: "Quick Rollback"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/incremental_restore.html"
last_updated: "3/5/2025"
product_version: "13.0.1.1071"
---

# Quick Rollback

In this article

When you restore a full VM or VM hard disk to the original location, you can instruct Veeam Backup & Replication to perform quick rollback — incremental data restore. Instead of restoring an entire VM or VM disk from a backup file, Veeam Backup & Replication will recover only those data blocks that are necessary to revert the VM or VM disk to an earlier point in time. Quick rollback significantly reduces the recovery time and has little impact on the production environment.

For quick rollback, Veeam Backup & Replication uses the Changed Block Tracking technology. Veeam Backup & Replication gets information about the current VM state and compares it with the CBT information in the backup file. This way, Veeam Backup & Replication detects what data blocks must be transported back to the production datastore to rebuild the VM or VM disk to the necessary point in time.

It is recommended that you use quick rollback if you restore a VM or VM disk after a problem that has occurred at the level of the VM guest OS — for example, there has been an application error or a user has accidentally deleted a file on the VM guest OS. Do not use quick rollback if the problem has occurred at the VM hardware level, storage level or due to a power loss.

Considerations and Limitations for Quick Rollback

* VM or VM disk must be restored to its original location.
* CBT must be enabled for the VM and its disks.

* Quick rollback can be performed in the Direct NFS access, Virtual appliance, Network transport mode. The Direct SAN access transport mode cannot be used for quick rollback due to [VMware limitations](https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-vddk-programming-guide/GUID-6D934561-189A-442B-9BA9-305096036D03.html).
* After quick rollback, CBT will be disabled for the restored VM.
* Use quick rollback and VM guest OS file exclusion wisely. If you exclude specific files and folders from the VM guest OS during backup and use quick rollback to restore the VM or VM disk from such backup, Veeam Backup & Replication will restore only the content of the backup file. The excluded data will not be restored. For example, if you exclude C:\Folder from the backup, data in this folder will not be backed up and will not be available in the resulting backup file. After some time, data in C:\Folder may change but the folder will still not be backed up (since the job excludes this folder). For this reason, when you perform quick rollback, Veeam Backup & Replication will restore all data that have changed except the excluded C:\Folder.

Related Topics

* [Performing Entire VM Restore](performing_full_recovery.md)
* [Restoring VM Hard Disks](performing_disk_restore.md)

Page updated 3/5/2025

Page content applies to build 13.0.1.1071
