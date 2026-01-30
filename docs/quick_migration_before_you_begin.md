---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/quick_migration_before_you_begin.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you perform Quick Migration, check the following prerequisites and limitations:

* Backup infrastructure components that will take part in Quick Migration must be added to the backup infrastructure and properly configured. These include the source and target ESXi hosts.
* The target datastore must have enough free space to store disks of the VMs that you plan to migrate. To receive alerts about low space on the target datastore, configure global notification settings. For more information, see [Specifying Global Notification Settings](global_notifications.md).
* Quick Migration is not possible for VMs that use SCSI bus sharing. This is because Quick Migration requires snapshots, which VMware does not support for such VMs.
* Disk format change is available only for VMs using virtual hardware version 7 or later.
* If you perform Quick Migration from a vSAN datastore, or if you store redo logs on a vSAN datastore during Instant Recovery, expect significant delays during migration. That is because of the specific way vSAN organizes data storage. Veeam Backup & Replication cannot get the difference between the source and target VM. Veeam Backup & Replication needs to read the entire disks instead of delta disks.
* If you want to use VMware vSphere vMotion to relocate VMs between hosts and VMware vSphere Storage vMotion to relocate VM disks between datastores, make sure that you have a VMware vSphere license covering these features.
* If you use tags to categorize virtual infrastructure objects, check limitations for VM tags. For more information, see [VM Tags](vm_tags.md).

Encryption

Veeam Backup & Replication does not keep encryption settings if a VM is migrated with VMware vMotion. After the migration process is finished, you will need to enable encryption for the migrated VM manually.

Integration with Instant Recovery

When you restore a VM using Instant Recovery, Veeam Backup & Replication starts the VM directly from a compressed and deduplicated backup file. To finalize recovery of a VM, you still need to move it to a new location. Moving the VM with VMware Storage vMotion or hot replication may require a lot of time and resources, or it may cause loss of valuable data.

Veeam Quick Migration was designed to complement Instant Recovery. Instead of pulling data from vPower NFS datastore, Quick Migration registers the VM on the target host, restores the VM contents from the backup file located in the backup repository and synchronizes the VM restored from backup with the running VM.

For more information, see [Instant Recovery to VMware vSphere](instant_recovery.md).

|  |
| --- |
| Note |
| Virtual appliance (HotAdd) transport mode cannot be used if the role of the backup proxy and mount server or backup repository where the backup file is stored are assigned to the same VM. |


