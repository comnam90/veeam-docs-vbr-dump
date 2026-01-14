---
title: "Backup for VMware Cloud Director"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_director_backup.html"
last_updated: "5/20/2025"
product_version: "13.0.1.1071"
---

# Backup for VMware Cloud Director

In this article

Veeam Backup & Replication allows you to create backups of the following instances:

* Regular, standalone and linked VMs
* vApps
* Organization VDCs
* Organizations
* VMware Cloud Director instances

When Veeam Backup & Replication performs backup, it captures vApp metadata. vApp metadata includes the following information: general information about the vApp in which the VMs reside, such as vApp name, description, VMs descriptions; information about vApp networks and organization networks to which the vApp is connected; VMs startup options; user information; lease; quota and other information. For more information on data backed up for VMs, see [Data to Back Up](vcloud_backup_data.md).

vApp metadata is stored together with the VM content. Capturing vApp metadata is critical for restore: without it, you will not be able to restore vApps and VMs back to VMware Cloud Director.

In Veeam Backup & Replication, backup is a job-driven process. To create a backup, you need to [configure a backup job](vcloud_director_perform_backup.md). The backup job is a configuration unit of the backup activity. The backup job defines when, what, how and where to back up. One backup job can be used to process one or multiple VMs. You can instruct Veeam Backup & Replication to run jobs automatically by schedule or start them manually.

|  |
| --- |
| Note |
| We recommend creating VMware Cloud Director backup jobs to back up VMs managed by VMware Cloud Director. If you back up VMs managed by VMware Cloud Director using a VMware vSphere backup job, Veeam Backup & Replication will perform a backup at the level of the underlying vCenter Server and will not capture vApp metadata. As a result, you will not be able to restore a fully functioning VM to VMware Cloud Director. |

Related Topics

* [Data to Back Up](vcloud_backup_data.md)
* [Adding VMware Cloud Director Servers](adding_vcloud_director.md)
* [Creating Backup Jobs for Cloud Director VMs](vcloud_director_perform_backup.md)
* [Data Recovery for VMware Cloud Director](vcloud_director_vm_restore.md)

Page updated 5/20/2025

Page content applies to build 13.0.1.1071
