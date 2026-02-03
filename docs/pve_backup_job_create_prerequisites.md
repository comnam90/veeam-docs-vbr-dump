---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_job_create_prerequisites.html"
last_updated: "1/27/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create a backup job, consider the following limitations:

* You can back up each VM with one backup job at a time. If a VM is already being processed by a backup job, another backup job will not start processing this VM until the currently running backup operation completes.

* You cannot back up a VM being restored. Wait for the restore process to complete, and then start the backup job.

* You cannot back up VMs created from [templates as linked clones](https://pve.proxmox.com/wiki/VM_Templates_and_Clones#Linked_Clone). Backup of full clones is supported.
* You cannot back up VMs with the same BIOS UUID.
* You cannot include into a backup job a VM that is being backed up by 3rd party software. Wait for the backup process to complete or stop the currently running job manually, and then add the VM to the necessary backup job.

* You cannot include into a backup job a resource pool that does not contain any VMs. Note that after you update a resource pool in the Proxmox VE administration portal, it may take up to 15 minutes for Veeam Plug-in for Proxmox VE to synchronize data between Proxmox VE and Veeam Backup & Replication.
* Veeam Plug-in for Proxmox VE does not support backup of iSCSI disks. If iSCSI disks are attached to a VM included into a backup job, these disks will be skipped from processing.
* Veeam Plug-in for Proxmox VE does not support backup of VM permissions granted to users, user groups and API tokens.
* By default, Veeam Plug-in for Proxmox VE [enables deduplication](compression_deduplication.md) for backed-up data. Due to technical limitations, you cannot disable it while configuring backup jobs.

* By default, [backup encryption](data_encryption.md) is disabled for backed-up data. However, you can enable encryption at the repository level as described in section [Access Permissions](access_permissions.md).

* Since Veeam Backup & Replication does not allow you to assign [information about locations](locations.md) to the Proxmox VE server and workers, job statistics do not include information on the Proxmox VE VM data migration between different geographic regions.


