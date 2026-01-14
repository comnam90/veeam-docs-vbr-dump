---
title: "em_disk_restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_disk_restore.html"
last_updated: "7/28/2023"
product_version: "13.0.1.1071"
---


In this article

Virtual disk restore may be helpful if a VM disk becomes corrupted for some reason. The restored virtual disk can be attached to the original VM to replace a corrupted drive, or connected to any other VM. For more information on virtual disk restore, see the [Virtual Disk Restore](https://helpcenter.veeam.com/docs/vbr/userguide/virtual_drive_recovery.html?ver=13) section of the Veeam Backup & Replication User Guide.

Users with the Portal Administrator role have no scope limitations. They can restore VM disks to their original location. Restore scope for other users is defined as described in the [Configuring Restore Scope](veeam_backup_em_restore_scope.md) section.

Before you restore virtual disks, consider the following:

* Disk restore is available in the Enterprise and Enterprise Plus editions of Veeam Backup & Replication.
* Disk restore is supported for backups of VMware vSphere VMs only.
* During the virtual disk restore, Veeam Backup & Replication powers off the target VM to reconfigure its settings and attach restored disks. It is recommended that you stop all activities on the target VM for the restore period.

To restore a VM disk from backup, use the Virtual Disk Restore wizard.

1. [Launch the Virtual Disk Restore wizard](em_disk_restore_launch.md).
2. [Select a restore point](em_disk_restore_restorepoints.md).
3. [Specify disk mapping](em_disk_restore_diskmapping.md).
4. [Specify secure restore settings](em_disk_restore_securerestore.md).
5. [Review the restore settings](em_disk_restore_summary.md).

Page updated 7/28/2023

Page content applies to build 13.0.1.1071
