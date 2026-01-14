---
title: "VMware Tools Quiescence"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tools_quiescence.html"
last_updated: "12/10/2024"
product_version: "13.0.1.1071"
---

# VMware Tools Quiescence

In this article

When you back up or replicate a running VM, you need to quiesce or ‘freeze’ the VM to bring its file system and application data to a consistent state. Data quiescence is crucial for highly-transactional applications. It helps create transactionally consistent backups or replicas and guarantees safety of application data.

To create consistent backups and replicas for VMs that do not support [Persistent VSS Snaphots](persistent_snapshots.md) (for example, Linux VMs), Veeam Backup & Replication uses the VMware Tools to freeze the file system and application data on VMs before it creates a backup or a replica. VMware Tools also allow you to create backups and replicas for Microsoft Windows-based VMs that support Microsoft VSS. For this, VMware Tools use VMware VSS component. For details on the supported OSes and quiescence features, see the [VMware documentation](https://docs.vmware.com/en/VMware-vSphere/8.0/vsphere-vddk-programming-guide/GUID-12AFEE64-4427-4127-9B1B-23F2948FD650.html).

To create transactionally consistent backups or replicas of VMs that do not support Microsoft VSS, you must define the following settings at the job level:

1. Enable VMware Tools quiescence. For more information on how to enable VMware Tools quiescence, see [vSphere Settings](backup_job_advanced_vsphere_vm.md).
2. Specify scripts that will bring applications to a transactionally consistent state before freezing and to the initial state after freezing VMs. For more information, see [Pre-Freeze and Post-Thaw Scripts](pre_post_scripts.md).

|  |
| --- |
| Note |
| By default, Veeam Backup & Replication uses [application-aware processing](application_aware_processing.md) when both VMware Tools quiescence and application-aware processing are enabled. If some VMs cannot be quiesced with application-aware processing or it is disabled for specific VMs in the job (the Disable application processing is set for VMs in the job settings), Veeam Backup & Replication uses VMware Tools quiescence to prepare these VMs for backup or replication. |

Related Topics

[Application-Aware Processing](application_aware_processing.md)

Page updated 12/10/2024

Page content applies to build 13.0.1.1071
