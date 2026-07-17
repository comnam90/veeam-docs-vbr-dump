---
title: "VM Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_backup_job_how.html"
last_updated: "2026"
product_version: "13.0.2.29"
---

# VM Backup


To produce backups of VMs, Veeam Plug-in for Scale Computing HyperCore runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

Veeam Plug-in for Scale Computing HyperCore does not install agent software inside VMs to back up VM data — it uses native Scale Computing HyperCore capabilities instead. During every backup session, Veeam Plug-in for Scale Computing HyperCore creates a Scale Computing HyperCore copy-on-write snapshot of each VM added to a backup job. The snapshot is further used to create a VM backup.

How to Protect VMs

1. Check [system requirements](platform_support_sch.md) and [account permissions](sch_permissions.md).
2. [Add backup repositories](sch_configure_repository.md).
3. [Connect the Scale Computing HyperCore cluster](sch_connecting_manager.md).
4. [Add workers](sch_workers_add.md).
5. Configure [email settings](sch_email_settings.md) and [notifications](sch_notifications.md).
6. [Configure a backup job](sch_backup_job_create.md).

How VM Backup Works

Veeam Plug-in for Scale Computing HyperCore performs VM backup in the following way:

1. Launches a worker on the same cluster where the processed VM resides.
2. Connects to the Scale Computing HyperCore cluster and creates a snapshot of the processed VM.
3. Uses the worker to read data from disks that are attached to the processed VM, compares it to the data written to the snapshot created at step 2, excludes the changes and transfers the resulting data to the target repository — and stores it in the native Veeam format.

To reduce the amount of data read from VM disks, Veeam Plug-in for Scale Computing HyperCore uses the changed block tracking (CBT) mechanism: during incremental backup sessions, Veeam Plug-in for Scale Computing HyperCore compares the current snapshot with the previous one and reads only those data blocks that have changed since the previous backup session. If CBT cannot be used, Veeam Plug-in for Scale Computing HyperCore reads all data from the VM disks. For more information, see [Changed Block Tracking](sch_changed_block_tracking.md).

Veeam Plug-in for Scale Computing HyperCore compresses and deduplicates data saved to repositories.

1. Removes the previous snapshot and suspends the worker when the backup session completes.

Related Topics

* [Solution Architecture](sch_infrastructure_components.md)
* [Backup Chain](sch_backup.md)
* [Retention Policies](sch_retention_policy.md)

Page updated 2026-07-14

