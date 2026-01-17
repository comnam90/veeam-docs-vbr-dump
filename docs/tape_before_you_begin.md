---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_before_you_begin.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you configure a backup to tape job, check the following prerequisites and limitations:

* You must have Veeam Backup & Replication Enterprise license or higher installed on the Veeam backup server.
* You must check configuration of source backup job(s). Tape jobs have the following requirements for the retention policy setting:

+ A source job with forever forward incremental chain must keep not less than 3 restore points on disk.
+ A source job with forward incremental chain must keep not less than 3 restore points on disk.
+ A source backup copy job in the immediate copy mode must keep not less than 3 restore points on disk.
+ A source backup copy job in the periodic copy mode must keep not less than 3 restore points on disk. If this job was created in Veeam Backup & Replication versions earlier than 12, it must keep not less than 4 restore points on disk.
+ A reverse incremental chain has no required minimum.

* You must configure one or more media pools with the necessary media set and retention settings.
* You must load tapes to the tape device and configure the target media pool so that it has access to them. If the media pool has no available tape, the tape job will wait for 72 hours and then terminate.
* The backup to tape job processes VBK (full backups), VIB files (forward incremental backups), and files and folders (if the source for the backup to tape job is an unstructured data backup job or repository that stores unstructured data backups).
* If you back up to tape a reverse incremental chain, the tape job will always copy the full backup. Reverse incremental backups (VRB) are skipped from processing.
* Microsoft SQL Server log files, Oracle log files and PostgreSQL log files (VLB) are skipped from processing.
* If a job is unable to complete within 21 days period, it will be stopped with the Failed status.
* Protecting [unstructured data backups with backup to tape jobs](btt_nas.md) does not consume Veeam license instances.
* [For Veeam Cloud Connect service providers] To back up tenants to tape, you must have Veeam Cloud Connect service provider license installed on the Veeam backup server.
* [For Veeam Cloud Connect service providers] The backup to tape job that backs up tenants to tape will not process backups created with previous versions of Veeam Backup & Replication or Veeam Agents. To avoid this, you must upgrade the tenants' backup server or agent machines to the last version. After the upgrade, the tenants' jobs must run at least once.

System Requirements for Backup to Tape Job

For processing backup to tape jobs, you must provide additional system resources apart from those listed in system requirements for the [backup server](system_requirements.md#backup_server) and [tape server](system_requirements.md#tape_server).

| Component | RAM | CPU Cores per Task |
| --- | --- | --- |
| Backup server | 1 GB1 plus 1 GB for each concurrent task | 1 |
| Source repository/gateway server | System resources depend on the job type:   * For backup to tape jobs, 250 MB - 350 MB (for source Veeam Data Mover) * For [backup to tape jobs for unstructured data backups](btt_nas.md), 6 GB for each tape drive2 | 0,5 |
| Tape server | 250 MB - 350 MB (for target Veeam Data Mover) | 0,5 |

1 Memory consumption varies according to the number of source jobs, number of VMs in these jobs, size of source backup metadata, and so on.

2 For more details, see [Tape Parallel Processing](parallel_processing.md).

System Requirements for Backup to Tape Job for Unstructured Data Backups

If the [backup to tape job for unstructured data backups](btt_nas.md) processes large quantities of files and objects, you must provide additional system resources apart from those listed in system requirements for the [backup server/database server](system_requirements.md#backup_server) and [tape server](system_requirements.md#tape_server).

For the database server to store the configuration database, we recommend using a dedicated NVME drive that is not used for anything else. The following minimum system requirements apply:

* CPU: 8 CPU cores.
* Memory: Same as for the backup server. If the database server and the backup server are the same server, double the RAM.
* Database Size: 850 MB for every 1 000 000 file and folder versions written to tape. A new file or folder version is created with each full backup run or if a file or folder was changed.

Page updated 1/15/2026

Page content applies to build 13.0.1.1071
