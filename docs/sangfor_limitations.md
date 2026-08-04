---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


When you plan to deploy and configure Veeam Plug-in for Sangfor aSV, keep in mind the following limitations and considerations.

Configuration

When configuring Veeam Plug-in for Sangfor aSV, consider the following:

* Veeam Plug-in for Sangfor aSV does not support user accounts with OpenID Connect authentication to access the Sangfor aSV server.
* The Sangfor aSV server must be able to establish a direct IP connection to the backup server. Connections through NAT gateways are not supported.

* Veeam Plug-in for Sangfor aSV does not support the IPv6 protocol.

* After you make changes to your Sangfor aSV environment (for example, you migrate a VM between cluster nodes), these changes may not appear in Veeam Backup & Replication immediately — the data synchronization process between the backup server and the Sangfor aSV server may take up to 15 minutes to complete. You can speed up the data synchronization process by [rescanning the Sangfor aSV server](sangfor_server_rescan.md).

Backup Repositories

When managing backup repositories, consider the following:

* Veeam Plug-in for Sangfor aSV does not support storing backups in Veeam Cloud Connect repositories. However, you can use them for [storing copies of backups](sangfor_backups_copy.md) created with Veeam Plug-in for Sangfor aSV.
* If a repository storing Sangfor aSV backups becomes an extent of a scale-out backup repository, the jobs targeting that repository will fail. You can edit the job to target a scale-out backup repository to fix the problem.

Workers

When configuring workers, consider the following:

* A worker can run a maximum of 63 parallel tasks and a minimum of 2. The maximum equals the Sangfor aSV per-VM limit of 64 disks minus the worker system disk.
* Only 13 parallel tasks per worker can use the HotAdd transport, because Sangfor aSV reserves 3 of the 16 IDE slots (ide0–ide2) for the worker system disks. Additional tasks run over the slower NBD over SSL transport.
* Deployment of 2 or more workers at a time may result in worker image upload failure.
* Worker deployment is not available to tenants with configured communication domains.
* If a job session fails, a worker snaphot from a failed session is not deleted and may require manual removal.

Backup

When protecting Sangfor aSV resources, consider the following:

* Veeam Plug-in for Sangfor aSV does not support backup of replicated VMs. These VMs are not included in the list of VMs on Veeam Backup & Replication side.
* Veeam Plug-in for Sangfor aSV does not support backup of shared virtual disks and physical disks. If such disks are attached to a VM included into a backup job, these disks will be skipped from processing.
* Veeam Plug-in for Sangfor aSV backup is not compatible with native Sangfor Cloud Platform backup. Simultanious backup jobs will result in error.

* If snapshot creation is disabled for the disks that are included in a backup job, those disks will be skipped during a job session.
* If at least one of the cluster nodes included in the connected Sangfor aSV server becomes inaccessible, backup processing of the whole cluster will be interrupted.
* You cannot assign locations to Sangfor aSV clusters in Veeam Backup & Replication. For that reason, job statistics do not include information on Sangfor aSV VM data migration between different geographic regions.
* Backup move is not supported for the Sangfor aSV backups.
* Retention of VeeamZIP backups is not supported.

* Backup job encryption is not supported.
* Encrypted VM backup is not supported.
* Sangfor Cloud Platform Groups cannot be selected as a backup scope.
* Backup of VMs without disks is not supported.
* Failed backup sessions may leave orphaned snapshots that require manual cleanup.
* Displayed backup session messages may appear in the wrong order.

Restore

When restoring Sangfor aSV resources, consider the following:

* Disk size over 63 TB is not supported.
* Restore of VMs with more than 64 vCPUs is not supported.
* Windows VMs with 5 or more disks including CD-ROMs are not supported.
* Restore of VMs with more than 63 disks is not supported.
* If you restore the VM from a backup stored in the archive tier of the scale-out backup repository, you must first retrieve backup data as described in section [Retrieving Backup Files](retrieval_job_launch.md). Note that you cannot perform Entire VM restore from backups stored in the archive tier that consists of the Amazon S3 Glacier Instant Retrieval extent. For those backups, you can perform Instant Recovery.

* You cannot restore VMs from backups stored in external repositories, Veeam Cloud Connect repositories, and on tapes.
* [SureBackup](surebackup_recovery_verification_hv.md) for backups created by Veeam Plug-in for Sangfor aSV is supported in the Backup verification and content scan only verification mode.
* Restore to an original location is possible only if the original VM still exists.
* Restore of VMs in the compatibility mode is not supported.
* Linked VMs cannot be restored to an original location.
* After a linked VM is restored to a new location, it becomes flattened.
* Network cannot be selected for a VM that is restored from an Archive tier.
* Due to delays in data synchronization between cluster, Sangfor Cloud Platform and Veeam Plug-in for Sangfor aSV, restore to original location may appear as available in UI while being restricted on the server site.
* Restore is not available to tenants with configured communication domains.

Page updated 2026-07-29

