---
title: "VM Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_backup_job_how.html"
last_updated: "3/2/2026"
product_version: "13.0.1.1071"
---

# VM Backup


To produce backups of VMs, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

Veeam Backup & Replication does not install agent software inside VMs to back up VM data — it uses native HPE Morpheus VM Essentials capabilities instead. During every backup session, Veeam Backup & Replication creates a HPE Morpheus VM Essentials copy-on-write snapshots of disks of each VM added to a backup job. The snapshots are further used to create a VM backup.

How to Protect VMs

1. Check [system requirements](hpe_system_requirements.md) and [account permissions](hpe_permissions.md).
2. [Add backup repositories](hpe_configure_repository.md).
3. [Connect the HPE Morpheus VM Essentials server](hpe_connecting_manager.md).
4. [Configure worker settings](hpe_workers_add.md).
5. [[Optional] Configure email settings and notifications](hpe_general_settings.md).
6. [Complete the New Backup Job wizard](hpe_backup_job_create.md).

How VM Backup Works

Veeam Backup & Replication performs VM backup in the following way:

1. Launches a worker on the same host where the processed VM resides.

If no worker is deployed on the host, Veeam Backup & Replication launches a worker that is deployed on any other HPE Morpheus VM Essentials host of the same HPE Morpheus VM Essentials server.

1. Connects to the HPE Morpheus VM Essentials manager and creates copy-on-write disk snapshots of the processed VM.
2. Uses the worker to read data from the snapshots of VM disks created at the step 2, transfers the data to the target backup repository and stores it in the native Veeam format.

To reduce the amount of data read from snapshots, Veeam Backup & Replication uses the changed block tracking (CBT) mechanism: during incremental backup sessions, Veeam Backup & Replication use native libvirt and QEMU mechanisms  to retrieve only those data blocks that have changed since the previous backup session. If CBT cannot be used, Veeam Backup & Replication reads all data from the snapshots. For more information, see [Changed Block Tracking](hpe_changed_block_tracking.md).

Veeam Backup & Replication compresses and deduplicates data saved to repositories.

1. Removes the created snapshot and shut downs the worker when the backup session completes.

Related Topics

* [Solution Architecture](hpe_infrastructure_components.md)
* [Backup Chain](hpe_backup.md)
* [Retention Policies](hpe_retention_policy.md)


