---
title: "em_managing_vms"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_managing_vms.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---


In this article

Authorized users can restore VMs included in their restore scope. Users with the Portal Administrator role have no scope limitations. The restore scope can be customized if you have the Enterprise Plus edition of Veeam Backup & Replication. In other editions, this list includes all machines and cannot be customized. However, you can delegate recovery of entire machines, guest files, or selected file types. Possible delegation options are described in the [Configuring Permissions for File and Application Item Restore](configuring_restrictions_for_restore.md) section.

With Veeam Backup Enterprise Manager, you can perform the following operations with machines:

* View machines and delete them from backups
* Create on-demand incremental backups (quick backups) for machines
* Restore machines and VM disks from backups
* Failover to VM replicas and VMware Cloud Director vApps
* Run failover plans for VMware vSphere and Microsoft Hyper-V VMs

|  |
| --- |
| Note |
| Veeam Backup Enterprise Manager does not display Nutanix AHV VMs, and recovery of Nutanix AHV VMs is not available. However, you can browse and restore guest OS files of Nutanix AHV VMs. For more information, see [Guest OS File Restore](searching_restoring_vm_guest_files.md). |

In This Section

* [Viewing Machines](viewing_vms.md)
* [Deleting Machine from Backup](deleting_machine.md)
* [Quick Backup](em_vm_quick_backup.md)
* [VM Recovery](vm_recovery.md)

Page updated 8/26/2025

Page content applies to build 13.0.1.1071
