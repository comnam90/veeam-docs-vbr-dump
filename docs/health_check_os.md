---
title: "Health Check for Object Storage Repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/health_check_os.html"
last_updated: "4/29/2025"
product_version: "13.0.1.1071"
---

# Health Check for Object Storage Repositories

In this article

You can instruct Veeam Backup & Replication to periodically perform a health check for the latest restore point in the backup chain. An automatic health check can help you verify that VM data blocks are present in the object storage repository and check the integrity of these blocks. It helps you avoid a situation where a restore point gets corrupted, making all dependent restore points corrupted, too. The health check helps ensure that the restore point is consistent, and you will be able to restore data from this restore point.

During a health check, Veeam Backup & Replication performs a cyclic redundancy check (CRC) for metadata and a hash check for VM data blocks in the backup file to verify their integrity. If during the health check Veeam Backup & Replication detects corrupted data blocks in the latest restore point in the backup chain, it will start the [health check retry](#retry). During the health check retry, Veeam Backup & Replication will transport valid data blocks from the source datastore (for VMware vSphere jobs) or volume (for Hyper-V jobs) to the object storage repository. After the health check retry completes, the transported data blocks are moved immediately to the latest backup in the backup chain.

To allow Veeam Backup & Replication perform the health check of data blocks located in the object storage repository, you must enable the health check when you configure a backup job and define its schedule. By default, the health check is performed on the last Friday of every month. You can change the schedule and run the health check weekly or monthly on specific days.

Considerations and Limitations

Consider the following limitations for the health check:

* The health check retry will start only if the backups job meets the [necessary requirements](#conditions). Otherwise, Veeam Backup & Replication will add healthy blocks to a new backup file after the next job run.
* We recommend that you configure a helper appliance to perform the health check for data blocks in object storage repositories. If you do not configure the helper appliance, Veeam Backup & Replication will use a mount server (for the direct connection mode) or a gateway server (for the gateway server connection mode) to perform the health check, which may result in additional costs. You can configure the helper appliance at the Mount Server step of the New Object Repository wizard.
* If you perform health check for encrypted backup files, Veeam Backup & Replication will pass encryption keys to the regular backup repository or cloud repository. For more information on encryption, see [Data Encryption](data_encryption.md).
* If you use Veeam Agent to back up machines and store their backups in object storage repositories, you can also perform the health check for Veeam Agent backups. For more information, see the Health Check for Object Storage section of the User Guide for Veeam Agent that you use to back up data.

* The health check runs only after all jobs and operations that process a backup are completed (for example, a backup job, a restore job, synthetic operations with backups and so on). If some of these activities are started, the health check stops.
* If the health check session does not complete until the next scheduled run, this session will stop and a new session will start according to the schedule.
* The health check skips verification of already processed data in case this data has not changed since previous health check session. For example, the source job did not process the backup chain after a health check completes. However, Veeam Backup & Replication verifies the metadata of backup files that did not change between health check sessions.

How Health Check Works

The health check is performed in the following way:

1. The health check starts according to the schedule.
2. Veeam Backup & Replication performs CRC values check for backup metadata, verifies that blocks of data is present in the object storage repository and checks their integrity.

During the health check, Veeam Backup & Replication verifies the restore point that represents the latest state of a VM and all data blocks that are required to perform the data recovery (restore point created by the current backup job session — the session during which the health check is performed). In this case, all data blocks that are required for the latest state of the VM in the active part of the backup chain are checked. If this restore point in the backup chain is incomplete, Veeam Backup & Replication checks the last complete restore point preceding the latest restore point.

1. If the health check does not detect data corruption, the backup job session completes in a regular way. If the health check detects corrupted data, Veeam Backup & Replication starts the health check retry process.

Depending on the revealed data corruption, Veeam Backup & Replication performs the following actions:

+ If the health check has detected corrupted backup metadata, Veeam Backup & Replication marks the whole backup chain as corrupted in the configuration database. In this case, you must detach the corrupted backup from the source job and run a backup job again to create a new backup chain.
+ If the health check detects corrupted blocks of data, Veeam Backup & Replication performs the health check retry and attempts to repair the corrupted data blocks.

Health Check Retry Mode

If the health check detects corrupted data, the backup job will switch to the Retry mode and will start the health check retry process. During the health check retry, Veeam Backup & Replication transports necessary data blocks of the whole VM image from the source datastore (for VMware vSphere jobs) or volume (for Hyper-V jobs) and saves transported data blocks to the latest backup file in the object storage repository.

If Veeam Backup & Replication does not perform the health check retry, you must retry the job manually. In this case, Veeam Backup & Replication produces a new backup file with healthy data blocks. You can use this backup file to restore from the latest restore point.

For scheduled jobs, the number of health check retries is equal to the number of job retries specified in the job settings. For jobs started manually, Veeam Backup & Replication performs 1 health check retry.

|  |
| --- |
| Important |
| To allow Veeam Backup & Replication add the repaired data blocks to the latest restore point after completing the health check, the backup job must meet the following requirements:   * The backup job must not be disabled. * You must schedule the backups job to run automatically. For more information, see the Schedule section for [VMware vSphere backup jobs](backup_job_schedule_vm.md) and [Microsoft Hyper-V backup jobs](backup_job_schedule_hv.md). * The target object storage is not set to the [Maintenance mode](sobr_maintenance.md). * Backup window settings must allow a backup job to run after the health check completes.   If the backup job does not meet these requirements, Veeam Backup & Replication will add the repaired data blocks to a new restore point, created during a next run of the backup job. |

Page updated 4/29/2025

Page content applies to build 13.0.1.1071
