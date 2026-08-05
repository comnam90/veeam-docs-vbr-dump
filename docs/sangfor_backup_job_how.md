---
title: "VM Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_backup_job_how.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VM Backup


To produce backups of VMs, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

Veeam Backup & Replication does not install agent software inside VMs to back up VM data — it uses native Sangfor aSV capabilities instead. During every backup session, Veeam Backup & Replication creates a Sangfor aSV copy-on-write snapshot of each VM added to a backup job. The snapshot is further used to create a VM backup.

How to Protect VMs

1. Check [system requirements](sangfor_system_requirements.md) and [account permissions](sangfor_permissions.md).
2. [Add backup repositories](sangfor_configure_repository.md).
3. [Connect the Sangfor aSV server](sangfor_connecting_manager.md).
4. [Configure worker settings](sangfor_workers_add.md).
5. [Configure email settings and notifications](sangfor_general_settings.md).
6. [Complete the New Backup Job wizard](sangfor_backup_job_create.md).

How VM Backup Works

Veeam Backup & Replication performs VM backup in the following way:

1. Launches a worker on the same host where the processed VM resides.

If no worker is deployed on the host, Veeam Backup & Replication launches a worker that is deployed on any other Sangfor aSV host connected to the backup infrastructure.

1. Connects to the Sangfor aSV server and creates a copy-on-write snapshot of the processed VM.
2. Uses the worker to read data from disks that are attached to the processed VM, compares it to the data written to the snapshot created at step 2, excludes the changes and transfers the resulting data to the target repository — and stores it in the native Veeam format.

To reduce the amount of data read from VM disks, Veeam Backup & Replication uses the changed block tracking (CBT) mechanism: during incremental backup sessions, Veeam Backup & Replication compares the current disk content with the backed-up content and reads only those data blocks that have changed since the previous backup session. If CBT cannot be used, Veeam Backup & Replication reads all data from the VM disks. For more information, see [Changed Block Tracking](sangfor_changed_block_tracking.md).

Veeam Backup & Replication compresses and deduplicates data saved to repositories.

1. Removes the created snapshot and suspends the worker when the backup session completes.

Related Topics

* [Solution Architecture](sangfor_infrastructure_components.md)
* [Backup Chain](sangfor_backup.md)
* [Retention Policies](sangfor_retention_policy.md)

Page updated 2026-07-14

