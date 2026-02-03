---
title: "VM Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_nutanix_integration.html"
last_updated: "1/9/2026"
product_version: "13.0.1.1071"
---

# VM Backup


To produce backups of VMs, Veeam Backup & Replication runs backup jobs. A backup job is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

While creating [image-level backups](ahv_data_protection.md#backupjob), Veeam Backup & Replication does not install agent software inside VMs to retrieve data. Veeam Backup & Replication uses [native Nutanix AHV capabilities](https://portal.nutanix.com/page/documents/details?targetId=Self-Service-Admin-Operations-Guide-v4_2_0:nuc-snapshot-restore-application-c.html) instead. During every backup session, Veeam Backup & Replication creates a Nutanix AHV live snapshot of each VM added to a backup job. The snapshot is further used to create a VM backup.

How to Protect VMs

1. Check [system requirements](ahv_system_requirements.md) and [account permissions](ahv_permissions.md).
2. [Add backup repositories](ahv_configure_repository.md).
3. [Connect the Nutanix AHV server](ahv_managing_clusters.md).
4. [Configure worker settings](ahv_workers_add.md).
5. [Complete the New Backup Job wizard](ahv_backup_job_create.md).

How VM Backup Works

Veeam Backup & Replication performs VM backup in the following way:

1. Connects to the Nutanix AHV server (Prism Central or Nutanix AHV cluster) over Nutanix AHV REST API and creates a [backup snapshot](ahv_nutanix_snapshots.md) of the processed VM.
2. Launches a worker on the same host where the processed VM resides.

If no worker is deployed on the host, Veeam Backup & Replication launches any other Nutanix AHV worker that is added to the backup infrastructure.

1. Re-creates VM disks from the snapshot created at step 1, adds them to a temporary volume group and attaches it to the worker.
2. Uses the worker to read data from disks of the volume group, transfers the data to the target repository and stores it in the native Veeam format.

To reduce the amount of data read from snapshots, Veeam Backup & Replication uses the changed block tracking (CBT) mechanism: during incremental backup sessions, Veeam Backup & Replication compares the new snapshot with the previous one and reads only those data blocks that have changed since the previous backup session. If CBT cannot be used, Veeam Backup & Replication reads all data from the snapshot. For more information, see [Changed Block Tracking](ahv_changed_block_tracking.md).

Veeam Backup & Replication compresses and deduplicates data saved to repositories.

1. Suspends the worker when the backup session completes.

|  |
| --- |
| Note |
| To limit the impact of backup tasks on network performance, Veeam Backup & Replication applies [network traffic throttling rules](network_rules.md) that prevent jobs from utilizing the entire bandwidth available in your environment. |

Related Topics

* [Solution Architecture](ahv_infrastructure_components.md)
* [Backup Chain](ahv_backup.md)

* [Snapshot Types](ahv_nutanix_snapshots.md)

* [Retention Policies](ahv_retention_policy.md)


