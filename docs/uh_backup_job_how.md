---
title: "VM Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_backup_job_how.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VM Backup


To produce backups of VMs, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

Veeam Backup & Replication does not install agent software inside VMs to back up VM data — it uses hypervisor capabilities instead. During every backup session, Veeam Backup & Replication creates copy-on-write snapshots of disks of each VM added to a backup job. The snapshots are further used to create a VM backup.

How to Protect VMs

1. Check [system requirements](uh_system_requirements.md) and [account permissions](uh_permissions.md).
2. [Add backup repositories](uh_configure_repository.md).
3. [Connect the universal hypervisor server](uh_connecting_manager.md).
4. [Configure worker settings](uh_workers_add.md).
5. [[Optional] Configure email settings and notifications](uh_general_settings.md).
6. [Complete the New Backup Job wizard](uh_backup_job_create.md).

How VM Backup Works

Veeam Backup & Replication performs VM backup in the following way:

1. Connects to the Universal Hypervisor Manager over REST API and creates a snapshot of the processed VM.
2. Launches a worker in the same cluster where the processed VM resides.

If no worker is deployed in the cluster, Veeam Backup & Replication launches a worker that is deployed in any other cluster connected to the Universal Hypervisor Manager. If the backup infrastructure contains another Universal Hypervisor Manager with deployed workers, Veeam Backup & Replication uses these workers instead.

1. Uses the worker to read VM data from the snapshot created at step 1, transfers the data to the target backup repository and stores it in the native Veeam format.

[Applies only to hypervisors that support CBT] To reduce the amount of data read from snapshots, Veeam Backup & Replication uses the changed block tracking (CBT) mechanism: during incremental backup sessions, Veeam Backup & Replication sends a REST API request to the Universal Hypervisor Manager to retrieve only those data blocks that have changed since the previous backup session. If CBT cannot be used, Veeam Backup & Replication reads all data from the snapshots. For more information, see [Changed Block Tracking](uh_changed_block_tracking.md).

Veeam Backup & Replication compresses and deduplicates data saved to repositories.

1. Removes the created snapshot, checks if any other tasks are in the queue and if there are no more sessions queued, suspends the worker when the current backup session completes.

Related Topics

* [Solution Architecture](uh_infrastructure_components.md)
* [Backup Chain](uh_backup.md)
* [Retention Policies](uh_retention_policy.md)

Page updated 2026-07-24

