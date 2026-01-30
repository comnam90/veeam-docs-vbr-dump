---
title: "About Backup Copy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/about_backup_copy.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# About Backup Copy


With backup copy, you can create several instances of the same backup file and copy them to secondary (target) backup repositories for long-term storage. Target backup repositories can be located in the same site as the source backup repository or can be deployed off-site. The backup copy file has the same format as the primary backup, so you can restore necessary data directly from it in case of a disaster.

Veeam Backup & Replication supports backup copy for the following types of backups:

* Backups of VMware vSphere or VMware Cloud Director virtual machines created by Veeam Backup & Replication.
* Backups of Microsoft Hyper-V virtual machines created by Veeam Backup & Replication.

* Backups of virtual and physical machines created by [Veeam Agent for Microsoft Windows, Veeam Agent for Linux, Veeam Agent for Mac, Veeam Agent for Oracle Solaris or Veeam Agent for IBM AIX](agents_introduction.md).

* Backups of Nutanix AHV virtual machines created by [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9).
* Backups of Oracle, SAP HANA, and Microsoft SQL Server databases created by [Veeam Plug-Ins for Enterprise Applications](protect_applications.md).
* Backups of MongoDB replica sets created by [MongoDB Backup](mongo_backup.md).
* Backups stored in an HPE StoreOnce backup repository.

* File share backups created by Veeam Backup & Replication.
* Backups of Proxmox VE VMs created by [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3).

* Backups of Amazon EC2 instances created by [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10).
* Backups of Microsoft Azure virtual machines created by [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1).
* Backups of VM instances created by [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\*.
* Backups created by [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*.
* Backups exported by [Kasten policies](https://helpcenter.veeam.com/docs/vbr/kasten_integration/overview.html?ver=13).
* Backups of Scale Computing HyperCore VMs created by [Veeam Plug-In for Scale Computing HyperCore](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2).

\* - Available on Microsoft Windows-based backup server.

|  |
| --- |
| Important |
| Consider the following for copying backups created by Veeam Backup for AWS, Veeam Backup for Microsoft Azure or Veeam Backup for Google Cloud:   * You can copy such backups from external repositories but not to them. * When copying backups from external repositories, consider that there can be a situation when new restore points were not copied. In this case, make sure the source chain for the backup copy job was not recreated. If it was recreated (all restore points have been deleted and created anew), you must create a new backup copy job with a new chain of backups. |

When the backup copying process starts, Veeam Backup & Replication accesses backup files in the source backup repository, retrieves data blocks for a specific machine from the backup file, copies them to the target backup repository, and composes copied blocks into a backup file in the target backup repository. The backup copying process does not affect virtual and physical infrastructure resources, does not require creation of additional VM snapshots or VSS snapshots and does not produce load on machines whose backups are copied.

Backup copy is a job-driven process. To copy backups, you need to configure backup copy jobs. The backup copy job defines when, what, how and where to copy. For more information on how to create backup copy jobs, see [Creating Backup Copy Jobs for VMs and Physical Machines](backup_copy_create.md). Note that to copy file share backups, you need to configure a file backup job, not the backup copy job. For more information, see [Creating File Backup Jobs](file_share_backup_job.md).

Related Topics

* [How Backup Copy Works](backup_copying_process.md)
* [Creating Backup Copy Jobs for VMs and Physical Machines](backup_copy_create.md)
* [Creating Backup Copy Jobs for HPE StoreOnce Repositories](backup_copy_hpe_storeonce.md)
* [Creating Backup Copy Jobs for Veeam Plug-Ins](backup_copy_plugins.md)


