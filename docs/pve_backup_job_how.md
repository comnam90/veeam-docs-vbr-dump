---
title: "VM Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_job_how.html"
last_updated: "2/20/2026"
product_version: "13.0.1.1071"
---

# VM Backup


To produce backups of VMs, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

Veeam Backup & Replication does not install agent software inside VMs to back up VM data — it uses native Proxmox VE capabilities instead. During every backup session, Veeam Backup & Replication creates a Proxmox VE copy-on-write snapshot of each VM added to a backup job. The snapshot is further used to create a VM backup.

How to Protect VMs

1. Check [system requirements](pve_system_requirements.md) and [account permissions](pve_permissions.md).
2. [Add backup repositories](pve_configure_repository.md).
3. [Connect the Proxmox VE server](pve_connecting_manager.md).
4. [Configure worker settings](pve_workers_add.md).
5. [Configure email settings and notifications](pve_general_settings.md).
6. [Complete the New Backup Job wizard](pve_backup_job_create.md).

How VM Backup Works

Veeam Backup & Replication performs VM backup in the following way:

1. Launches a worker on the same host where the processed VM resides.

If no worker is deployed on the host, Veeam Backup & Replication launches a worker that is deployed on any other Proxmox VE host connected to the backup infrastructure.

1. Connects to the Proxmox VE server and creates a copy-on-write snapshot of the processed VM.
2. Uses the worker to read data from disks that are attached to the processed VM, compares it to the data written to the snapshot created at the step 2, excludes the changes and transfers the resulting data to the target repository — and stores it in the native Veeam format.

To reduce the amount of data read from VM disks, Veeam Backup & Replication uses the changed block tracking (CBT) mechanism: during incremental backup sessions, Veeam Backup & Replication compares the current disk content with the backed-up content and reads only those data blocks that have changed since the previous backup session. If CBT cannot be used, Veeam Backup & Replication reads all data from the VM disks. For more information, see [Changed Block Tracking](pve_changed_block_tracking.md).

Veeam Backup & Replication compresses and deduplicates data saved to repositories.

1. Removes the created snapshot and suspends the worker when the backup session completes.

Related Topics

* [Solution Architecture](pve_infrastructure_components.md)
* [Backup Chain](pve_backup.md)
* [Retention Policies](pve_retention_policy.md)


