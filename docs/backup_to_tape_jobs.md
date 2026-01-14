---
title: "Backup to Tape"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_to_tape_jobs.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Backup to Tape

In this article

To back up data to tape, you need to create and run tape jobs. The backup to tape job is a dedicated job that archives to tape Veeam backups that were produced by Veeam backup jobs. Note that you cannot directly backup virtual machines to tapes.

|  |
| --- |
| Note |
| Support of the backup to tape is included in the Veeam Universal License. When using a legacy socket-based license, the Enterprise or Enterprise Plus edition of Veeam Backup & Replication is required. For details, see [Veeam Editions Comparison](https://www.veeam.com/backup-version-standard-enterprise-editions-comparison.html). |

You can archive the following data to tape:

* VM backups
* Unstructured data backups. For more details, see [Backup to Tape for Unstructured Data Backups](btt_nas.md)
* Veeam Agent backups
* Physical machine backups
* Backup repositories, including hardened repositories
* [For Veeam Cloud Connect] Tenants

The backups that can be archived to tapes also include those created with backup jobs that directly write backup data to object storage repositories.

When a backup to tape job runs, it does not create new backups: it locates already existing backups and copies them from backup repository to tape. You need to set the source of the tape job: jobs or backup repositories.

Sources of Backups for Backup to Tape Jobs

You can use several options for selecting backups that you want to write to tape with the tape job.

Jobs as Source

The following jobs can be a source for tape jobs:

* VMware/Hyper-V/Nutanix AHV/RHV/Proxmox VE backup jobs
* VMware/Hyper-V/Nutanix AHV/RHV/Proxmox VE backup copy jobs
* Unstructured data backup jobs
* Windows/Linux/Unix/Mac Veeam Agent backup jobs configured in Veeam Agent operating in the standalone mode
* Windows/Linux/Unix/Mac Veeam Agent standalone backup copy jobs
* Windows/Linux/Unix/Mac Veeam Agent backup jobs configured in Veeam Backup & Replication

* Veeam Agent backup jobs managed by the backup server
* Veeam Agent backup jobs managed by Veeam Agent (backup policy)

* Windows/Linux/Unix/Mac Veeam Agent backup copy jobs
* Cloud VM (Veeam Backup for Microsoft Azure/AWS/Google Cloud) backup copy jobs configured in Veeam Backup & Replication
* Kasten policies
* Backup copy jobs for Kasten policy

|  |
| --- |
| Note |
| Consider the following:   * [VeeamZIP backup jobs](veeamzip.md) can be archived to tape only with File to Tape jobs. VeeamZIP backup jobs cannot be a source for backup to tape jobs. For more information, see [File Backup to Tape](file_to_tape_jobs.md). * Backup to tape jobs can process only Veeam Agent backup jobs that are targeted to a Veeam backup repository. * [Microsoft Entra ID tenant backups](https://helpcenter.veeam.com/docs/backup/entraid/) and backups produced by [Veeam Plug-ins for Enterprise Applications](https://helpcenter.veeam.com/docs/backup/plugins/overview.html) cannot be a source for backup to tape jobs and are skipped from processing even if you add a repository as a source for tape jobs. |

When the tape job starts on its schedule, it picks the restore points that were produced by the source jobs in period since the last tape job run. If you change the configuration of the source jobs, the tape job is updated automatically: it adds new machines or folders and files to the list of entities to archive or stops archiving entities that were removed from source jobs.

The tape job will process its source jobs in alphabetical order.

Backup Repositories as Source

|  |
| --- |
| Note |
| When using backup repositories as a source for backup to tape, only [supported backup types](#supported_backups) can be archived to tape. |

When you add a repository as a source to a tape job, the tape job constantly scans the selected repository (or repositories) and writes the newly created backups to tape. The tape job monitors the selected repository in a background mode. You can set explicit backup windows for the tape job. In this case, the tape job will start on the set time and archive all new restore points that were created in the period since the last job run.

If you create or remove backup jobs that use this repository, or if you change the configuration of such backup jobs, you do not need to reconfigure the tape job that archives the repository.

Tenants as Source

This option is available for Veeam Cloud Connect service providers. Service providers can back up tenants backups from cloud repositories to tape. As the source to the backup to tape job, you can add tenants or cloud repositories. For more information, see the [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/backup/cloud/cloud_overview.html?ver=120) guide.

For tenants backups, only GFS media pools are used. For more information, see [GFS Media Pools](gfs_media_pools.md).

Mixed Jobs

To the one tape job, you can link an unlimited number of sources. You can mix source jobs of different types (backup jobs, backup copy jobs, file backup jobs) and on different platforms (VMware, Hyper-V, Windows Agent, Linux Agent). You can add jobs and repositories as source to the same tape job.

Also, you can add an unlimited number of tenants to the one tape job. However, you cannot mix tenants with backup jobs and backup repositories.

|  |
| --- |
| Important |
| The tape job looks only for the Veeam backups that are produced by backup jobs running on your console. Other files will be skipped. |

Linking Source Jobs

Linking tape jobs with source jobs is not obligatory when you create a tape job. You can add source jobs to tape jobs at any moment:

* If you already have backup jobs configured, you can choose the necessary jobs in the Backup to Tape Job wizard. For details, see [Creating Backup to Tape Jobs](creating_backup_to_tape_jobs.md).
* Alternatively, you can link an "empty" tape job or an existing tape job as a secondary destination target for the source backup job. For details, see [Linking Backup Jobs to Backup to Tape Jobs](linking_backup_to_backup_to_tape.md).

Source Job Backup Methods

The source jobs that create backups to be archived to tapes may use any backup method, no matter whether you select jobs, backup repositories or tenants as a source:

* [Forever forward incremental backup method](incremental_forever_backup.md)

To back up the forever forward incremental chains to tape, the tape job uses the virtual full. The virtual full creates a synthetic full backup on tape regularly (for example, once a week) and splits the chain into short series of tapes which is more convenient for restore. For more information, see [Virtual Full Backup](virtual_full_backup.md).

[For backup copies in periodic mode created in Veeam Backup & Replication versions earlier than 12] If the source job is a backup copy job in the periodic copy mode, note that the last restore point of the backup copy job stays active until the next restore point is created. The tape job does not copy such active points, because they may be updated. For this reason, the backup chain on tape will be always one restore point shorter than on disk.

* [Forward incremental backup method](forward_incremental_backup.md)

When the tape job backs up the forward incremental chain to tape, it creates a copy of the disk backup chain.

* [Reverse incremental backup method](reversed_incremental_backup.md)

The last backup in the reverse incremental backup chain is always the full backup. If the source backup chain is reverse incremental, the tape job will copy the full backup each time the tape job runs. The increments are skipped.

Related Topics

* [How Backup to Tape Works](backup_to_tape_hiw.md)
* [Backup to Tape for Unstructured Data Backups](btt_nas.md)
* [Creating Backup to Tape Jobs](creating_backup_to_tape_jobs.md)
* [Linking Backup Jobs to Backup to Tape Jobs](linking_backup_to_backup_to_tape.md)

Page updated 10/20/2025

Page content applies to build 13.0.1.1071
