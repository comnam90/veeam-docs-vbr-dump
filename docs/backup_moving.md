---
title: "Backup Move"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_moving.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Backup Move


Veeam Backup & Replication allows you to move all backups of a backup job to another repository or to move specific workloads and their backups to another job.

Moving backups to another repository can be helpful if you are running out of free space on a repository and want to move all backups created by a backup job to another repository, target the backup job to this repository and continue the backup chain.

Moving workloads and their backups to another backup job can be helpful if you want to separate one backup job into multiple backup jobs or if you want to change backup settings for specific workloads. Also, you want to continue the existing backup chains for the workloads.

How Moving to Another Repository Works

When moving backups to another repository and targeting the job to this repository, Veeam Backup & Replication performs the following:

1. Disables the backup job.
2. Copies backup files to a new location.
3. Targets the backup job to the new location.
4. Deletes source backup files.
5. After the successful move, Veeam Backup & Replication enables the backup job. The enabled backup job continues the backup chain for the existing and moved backups.

|  |
| --- |
| Note |
| The described algorithm is common. Nuances, requirements and limitations are described further in this section. |

How Moving to Another Job Works

When moving backups to another job, Veeam Backup & Replication performs the following:

1. Disables the source and target jobs.
2. If backups are moved within one repository without immutability, Veeam Backup & Replication invokes the native move method of the file system. This applies if the repository is Windows, Linux, CIFS, NFS, deduplicating storage appliance or a scale-out backup repository of one of the listed types. In other cases, Veeam Backup & Replication copies backup files of selected workloads to the repository where the target job saves backups.
3. Excludes the selected workloads from being processed by the source job.
4. Includes the selected workloads to be processed by the target job.
5. After the successful move, Veeam Backup & Replication enables the source and target jobs. The target backup job continues the backup chain for the existing and moved backups.

|  |
| --- |
| Note |
| The described algorithm is common. Nuances, requirements and limitations are described further in this section. |

Considerations and Limitations

This section lists considerations and known limitations for different types of jobs and different types of repositories where backups can be stored.

Common Considerations

Consider the following:

* You can move individual workloads and their backups only if backups are [per-machine backups](per_vm_backup_files.md) with separate metadata files and only to repositories with the Use per-machine backup files check box enabled.
* You can move backups between repositories with the Use per-machine backup files check box selected and not selected. However, the move operation does not change the [backup chain format](per_vm_backup_files.md) (single-file backup, per-machine backup with single metadata file or per-machine backup with separate metadata files). The job will continue the backup chain of the original backup chain format.

[For Windows-based backup servers] If you want to change the backup chain format of the chain, use the detach from job operation. For more information, see [Upgrading Backup Chain Formats](backup_change_type.md).

[For moving to object storage repositories] You can move only per-machine backups with separate metadata files.

* [For VeeamZIP] You cannot move VeeamZIP backups to direct object storage repositories or when they are added as the performance tier of a scale-out backup repository. However, you can still move VeeamZIP backups to object storage repositories used as the capacity or archive tiers.

* After you move workloads and their backups between jobs, you must adjust the guest processing settings for the moved workloads. After the move, Veeam Backup & Replication uses the default guest processing setting. For more information on guest processing settings, see [Guest Processing](guest_processing.md).
* You cannot move a workload and its backups to a job that already processes this workload.
* You cannot move backups from encrypted jobs to unencrypted jobs and vice versa.
* You cannot move backups imported without the metadata (.VBM) file.
* You cannot launch the restore operation for backups that are being moved at the moment.
* You cannot move backups from an HPE StoreOnce repository used as a target for a [backup copy for HPE StoreOnce repositories](backup_copy_hpe_storeonce.md).
* [For Microsoft Windows-based backup servers] You cannot move backups created by backup copy jobs in the legacy periodic copy mode. To move backups, you first need to upgrade the backup format as described in section [Upgrading Backup Chain Formats](backup_copy_change_type.md).

* After you move backups between backup copy jobs, Veeam Backup & Replication does not include and exclude workloads from the backup copy jobs. You should do that manually.

* You cannot move backups created by [Veeam Plug-Ins for Enterprise Applications](protect_applications.md), Veeam Cloud Plug-Ins ([Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10), [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\*, [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1)), [Veeam Plug-In for Nutanix AHV](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9), [Veeam Backup for OLVM and RHV](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*, [Veeam Plug-In for Proxmox VE](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3) and [Veeam Kasten](https://helpcenter.veeam.com/docs/vbr/kasten_integration/overview.html?ver=13).

\* Available only for Microsoft Windows-based backup servers.

* You cannot move [Unstructured Data Backups](unstructured_data_backup.md).

* You cannot move backups created from the vSphere Self-Service Backup Portal.
* You cannot move backups created in the Veeam Cloud Connect repositories. For more information on Veeam Cloud Connect repositories, see the [Cloud Repository](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_repository.html?ver=13) section in the Veeam Cloud Connect Guide.
* The Move backup operations to, from and between cloud repositories are not supported. For more information on Veeam Cloud Connect's limitations, see the [Veeam Cloud Connect Backup](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_limitations.html?ver=13) section in the Veeam Cloud Connect Guide.
* To use the move to another repository functionality and move backups to an object storage repository, check that [defragment and compact full backup file](backup_compact_file.md), [reverse incremental backup method](reversed_incremental_backup.md) and [synthetic full backup](synthetic_full_backup.md) are disabled for the job. Alternatively, you can use the move to another job functionality and move backups to a job already targeted to an object storage repository.
* Before moving workloads and their backups to a deduplicating storage appliance, Veeam Backup & Replication checks whether such a move can damage the backup chain. If so, Veeam Backup & Replication prohibits the move operation. After Veeam Backup & Replication completes the move operation, it checks that the target backup job is configured correctly. However, you must change the settings manually. You can find which backup settings need to be changed in the move session or in [this Veeam KB article](https://www.veeam.com/kb1745). For more information on how to view session statistics, see [Viewing Job Session Results](session_results.md).
* You can move VMware Cloud Director backups of a whole job or individual vApps. You cannot move backups of VMs.

* You cannot move Cloud Director vApp backups that are not linked to a job.

* If you move workloads and their backups between jobs linked to the same tape job, the tape job continues to create incremental backups within the existing backup chain. Otherwise, the tape job will create an active full backup for the moved workloads.
* [Traffic throttling](setting_network_traffic_throttling.md) is not supported for backup move operations.

Backup Jobs with Linked Backup Copy Jobs

If you move workloads and their backups from a backup job that is linked to a backup copy job, the following applies:

* If the source and target backup jobs are linked to backup copy jobs, Veeam Backup & Replication also moves backups and workloads between backup copy jobs. Note that Veeam Backup & Replication only performs the move if each backup job is linked to one backup copy job. For example, Backup Job 1 processes VM1 and VM2 and is linked to Backup Copy Job 1. Backup Job 2 processes VM3 and VM4 and is linked to Backup Copy Job 2. You move VM1 and its backups to the Backup Job 2. Veeam Backup & Replication will also move the VM1 and its backups from Backup Copy Job 1 to Backup Copy Job 2. As a result, Backup Job 2 and Backup Copy Job 2 will process VM3, VM4 and VM1.

If a backup job is linked to multiple backup copy jobs, you need to move workloads and backups between the backup copy jobs manually. To do that, use the move to another job operation as described in section [Moving Backups](move_backup.md). If you do not move workloads between backup copy jobs, the backup copy job linked to the target backup job will create active full backup copies for the moved workloads.

* If the source backup job is still in progress, the move operation fails.
* Before moving backup copies, Veeam Backup & Replication waits till the source move backup process finishes successfully. Only then will Veeam Backup & Replication disable the linked backup copy job and move backup copies.

Log Backups

If you move workloads and their backups from a backup job for which log backup is configured, the following applies:

* Veeam Backup & Replication moves log backups along with workloads.
* Veeam Backup & Replication disables the log backup jobs gracefully before moving log backups.
* [For SQL server Always On availability groups] You cannot move individual nodes from a job.
* [For Oracle Data Guard] You must move all servers from the job. If you move only one server, the application item restore stops working. To repair the application item restore functionality, you will need to move the server back to the original job.
* If guest processing is disabled in the target job, log backups are moved, however they will not be processed by the target job. To process log backups, make sure that guest processing is enabled for the target job as described in section [Specify Guest Processing Settings](backup_job_vss_vm.md).

Backups with GFS Flags

If you move backups from a backup or backup copy job where long-term (GFS) retention is configured, the following applies:

* When you move all backups to another repository, Veeam Backup & Replication preserves all backups with GFS flags.
* When you move a workload and its backups to another job, Veeam Backup & Replication starts to retain backups according to the settings configured in the target job. Veeam Backup & Replication deletes all GFS backups that do not comply with the retention policy in the target job. For example, if yearly backups are not configured in the target job, Veeam Backup & Replication will remove them after the move operation finishes.

Agent Backups

For more information on moving Veeam Agent backups, see the [Moving Backups](agent_backup_move.md) section in Veeam Agent Backup.

Immutable Repositories

If you move workloads and their backups from a repository for which immutability is enabled, the following applies:

* During the move operation, Veeam Backup & Replication copies the whole backup chain. After the move operation finishes, original backups stored in the immutable repository are moved to the node with the (Orphaned) postfix.
* Veeam Backup & Replication retains backups moved to the (Orphaned) node according to the retention period specified in the job from which the backups were moved. If the retention period is shorter than the immutability period specified in the repository settings where the backups were stored, Veeam Backup & Replication sets the retention period as equal to the immutability period.

If the retention period is set in days, Veeam Backup & Replication deletes a backup after its retention period ends. If the retention period is set in restore points, Veeam Backup & Replication does not delete backups. You can delete these backups manually after the retention period ends.

If you move a backup chain to a repository with different immutability or retention settings, Veeam Backup & Replication will replace the source repository settings with the settings of the target repository for that specific backup chain.

Scale-Out Backup Repositories

If you move workloads and their backups from a scale-out backup repository, the following applies:

* Veeam Backup & Replication moves backups only from the performance tier. If you want to move data from the capacity tier, you must first download it to the performance tier. For more information, see [Downloading Data from Capacity Tier](downloading_from_capacity_tier.md).
* Veeam Backup & Replication does not support moving backups between extents of a scale-out backup repository. To learn how to manage backups within the scale-out backup repository, see [Scale-Out Backup Repositories](backup_repository_sobr.md).
* Backups stored in the capacity and archive tiers are moved to the node with the (Orphaned) postfix. The backups are retained according to the retention settings of the job from which the backups were moved. If the retention period is set in days, the Veeam Backup & Replication retains the backups according to the configured retention and deletes the backups from the repository after the retention period ends. If the retention period is set in restore points, Veeam Backup & Replication leaves backup files in a backup chain. The minimum number of backup files left equals the current retention period. You can delete these backup files manually as described in section [Deleting Backups from Disk](delete_backup_from_disk.md).
* Veeam Backup & Replication does not move backups from extents in the Maintenance mode.

Related Topics

* [Moving Backups](move_backup.md)
* [Copying Backups](copy_backup.md)


