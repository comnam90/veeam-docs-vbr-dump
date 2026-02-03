---
title: "Snapshot Types"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_nutanix_snapshots.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Snapshot Types


In terms of data protection, Veeam Backup & Replication allows you to create the following types of snapshots:

* Backup snapshots

A backup snapshot is a VM snapshot created by a [backup job](ahv_backup_job_create.md). Backup snapshots are displayed in the Veeam Backup & Replication console, and can be used to perform [entire VM restore](ahv_restore_to_ahv.md) and [disk restore](ahv_restore_disks.md).

Backup snapshots allow Veeam Backup & Replication to use the [CBT mechanism](ahv_changed_block_tracking.md) while creating backups and to speed up the restore process (in comparison to restore from image-level backups).

* Snapshots

A snapshot is a VM snapshot taken manually in the Prism Element or Prism Central console. Snapshots are displayed in the Veeam Backup & Replication console. You can use snapshots to [restore VMs to the original Nutanix AHV environment](ahv_restore_to_ahv.md).

While taking VM snapshots, Nutanix AHV captures data residing on virtual disks attached to the VMs. To protect data residing on volume groups that are attached to the VMs, volume group (VG) snapshots or protection domain (PD) snapshots are created. VG snapshots capture data of volume groups only, whereas PD snapshots capture data of consistency groups that include VMs and volume groups attached to them.

* Snapshots on Replica Sites

[Applies only to the [Prism Central deployment](ahv_infrastructure_prism_central.md)] A snapshot on a replica site is a VM snapshot created and replicated by a Prism Central [protection policy](https://portal.nutanix.com/page/documents/details?targetId=Prism-Central-Guide-vpc_7_3:mul-explore-protection-policies-view-pc-r.html). Snapshots on replica sites are not displayed in the Veeam Backup & Replication console — these snapshots can be only be found in the Prism Central console.

Snapshots on replica sites allow Veeam Backup & Replication to reduce the backup load on the production environment. However, Veeam Backup & Replication can use these snapshots only if the following requirements are met for each VM included into the backup scope:

* No volume groups are attached to the VM.
* At least one VM snapshot has been replicated to a remote location since the most recent backup was created.
* The VM disk configuration has not changed since the most recent snapshot was replicated to a remote location.
* Guest processing is disabled for the backup job.

If any of those conditions are not met, Veeam Backup & Replication performs backup using [VM snapshots](#backup_snapshot) created by backup jobs in the main site.

* VG snapshots

A VG snapshot is a volume group snapshot created by a [backup job](ahv_backup_job_create.md) to produce VM backups. Veeam Backup & Replication takes VG snapshots only if the backup scope includes individual virtual machines with volume groups attached.

VG snapshots are not displayed in the Veeam Backup & Replication console. VG snapshots allow Veeam Backup & Replication to use the [CBT mechanism](ahv_changed_block_tracking.md) while creating backups and to [restore VMs with volume groups](ahv_restore_to_ahv.md).

* PD snapshots

A PD snapshot is a protection domain snapshot created to protect data of consistency groups (VMs and volume groups) included into a protection domain. PD snapshots guarantee the consistency of VM and volume group data. Starting from version 8, Veeam Plug-in for Nutanix AHV does not takes PD snapshots — if a PD is included into the backup scope, Veeam Plug-in for Nutanix AHV backs up VMs and their volume groups as if processing individual virtual machines.

|  |
| --- |
| Note |
| [Recovery points](https://portal.nutanix.com/page/documents/details?targetId=Prism-Central-Guide-vpc_7_3:mul-vm-manage-acropolis-pc-t.html) created manually in the Prism Central console cannot be used to protect and recover Nutanix AHV resources with Veeam Backup & Replication. |

In terms of data consistency, Veeam Plug-in for Nutanix AHV allows you to create the following types of snapshots:

* Crash-consistent snapshots

A crash-consistent snapshot contains the data of virtual disks and volume groups attached to a VM.

* Application-consistent snapshots

An application-consistent snapshot contains not only the data of virtual disks and volume groups attached to a VM, but also the data of applications (such as Microsoft Active Directory, Microsoft SQL Server, Microsoft SharePoint, Microsoft Exchange and Oracle) running in the VM guest OS, which allows you to restore the applications without data loss and corruption.

By default, Veeam Plug-in for Nutanix AHV always tries to create an application-consistent snapshot using [Nutanix Guest Tools](ahv_backup_job_vbr_advanced.md) when processing a VM. However, if the [requirements for application-consistent snapshots](https://portal.nutanix.com/page/documents/details?targetId=Prism-Element-Data-Protection-Guide-v7_3:wc-dr-application-consistent-snapshots-wc-r.html) are not met, Veeam Plug-in for Nutanix AHV creates a crash-consistent snapshot instead.

|  |
| --- |
| Tip |
| As an alternative to application-consistent snapshots, Veeam Plug-in for Nutanix AHV allows you to leverage native Veeam capabilities to create [application-consistent backups](ahv_backup_job_vbr_guest_processing.md). |


