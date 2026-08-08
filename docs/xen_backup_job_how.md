---
title: "VM Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/xen_backup_job_how.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VM Backup


To produce backups of VMs, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

Veeam Backup & Replication does not install agent software inside VMs to back up VM data — it uses native Xen capabilities instead. During every backup session, Veeam Backup & Replication creates Xen copy-on-write snapshots of disks of each VM added to a backup job. The snapshots are further used to create a VM backup.

How to Protect VMs

1. Check [system requirements](xen_system_requirements.md) and [account permissions](xen_permissions.md).
2. [Add backup repositories](xen_configure_repository.md).
3. [Connect the Xen pool](xen_server_connect.md).
4. [Configure worker settings](xen_workers_add.md).
5. [Configure email settings and notifications](xen_general_settings.md).
6. [Complete the New Backup Job wizard](xen_backup_job_create.md).

How VM Backup Works

Veeam Backup & Replication performs VM backup in the following way:

1. Launches a worker on the same host where the processed VM resides.

If no worker is deployed on the host, Veeam Backup & Replication launches a worker that is deployed on any other Xen host connected to the backup infrastructure and residing in the same pool as the processed VM.

1. Connects to the Xen pool and creates a copy-on-write snapshot of the processed VM.
2. Uses the worker to read VM data from the snapshot created at step 2, transfers the data to the target backup repository and stores it in the native Veeam format.

To reduce the amount of data read from VM disks, Veeam Backup & Replication uses the changed block tracking (CBT) mechanism: during incremental backup sessions, Veeam Backup & Replication compares the current disk content with the backed-up content and reads only those data blocks that have changed since the previous backup session. If CBT cannot be used, Veeam Backup & Replication reads all data from the VM disks. For more information, see [Changed Block Tracking](xen_changed_block_tracking.md).

Veeam Backup & Replication compresses and deduplicates data saved to repositories.

1. Removes the created snapshot and stops the worker when the backup session completes.

Related Topics

* [Solution Architecture](xen_infrastructure_components.md)
* [Backup Chain](xen_backup.md)
* [Retention Policies](xen_retention_policy.md)

Page updated 2026-07-29

