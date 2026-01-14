---
title: "Backup of Database Availability Groups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_dag_hiw.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# Backup of Database Availability Groups

In this article

The procedure of adding a Microsoft Exchange Database Availability Group (DAG) to a Veeam Agent backup job differs depending on the type of the DAG that you want to process:

* For a regular DAG, the backup job configuration procedure is the same as for any failover cluster. To process a regular DAG, you must configure a Veeam Agent backup job for a failover cluster. To learn more, see [Backup and Restore of Failover Clusters](agents_cluster_backup_and_restore.md).
* For an IP Less DAG (a DAG without an Administrative Access Point), the backup job configuration procedure is similar to the same procedure for standalone servers. To process an IP Less DAG, you must create a protection group with all nodes of the IP Less DAG and add this protection group to the Veeam Agent backup job managed by the backup server. To learn more, see [Creating Job for Windows Computers](agent_job_create_win.md).

How It Works

During backup, Veeam Agent performs the following operations:

1. Veeam Agent detects Microsoft Exchange Server.

Keep in mind that Veeam Agent performs the backup, but all pre-/post-backup operations are performed by the Exchange VSS Writer that is available on any Microsoft Exchange Server. To learn more about Exchange VSS Writer, see [Microsoft documentation](https://docs.microsoft.com/en-us/exchange/client-developer/backup-restore/exchange-writer-in-exchange-2013?redirectedfrom=MSDN).

To learn more about Exchange data backups, see [this Microsoft article](https://techcommunity.microsoft.com/t5/exchange-team-blog/everything-you-need-to-know-about-exchange-backups-part-1/ba-p/600223).

1. Veeam Agent detects that server added to the backup scope is a part of a DAG.

* For a regular DAG, Veeam Agent gets the list of all DAG servers and adds these servers to the backup job.

If a set of servers, that are included in a regular DAG, changes between the job runs, Veeam Agent changes the backup scope accordingly.

* For an IP less DAG, you must add all servers of an IP less DAG to the backup job manually.

|  |
| --- |
| IMPORTANT |
| An IP less DAG does not have an Administrative Access Point. As a result, you must add all servers of an IP less DAG to the protection group manually. If a set of servers included in an IP less DAG changes between the job runs, you must update the backup scope manually as well. Otherwise, Veeam Agent will still back up all database files from all servers included into backup scope, but Microsoft Exchange Server will detect data inconsistency and skip the database processing. |

1. Veeam Agent processes databases to prepare them for backup: Veeam Agent freezes databases, creates database snapshots, and returns databases to the initial state.

DAG servers contain active and passive copies of each database. By default, the Exchange VSS Writer issues VSS freeze commands to passive database copies only. If all passive copies of the database are not available for some reason, the Exchange VSS Writer issues the VSS freeze command to the active copy of the database. This approach helps to ensure data consistency.

1. After the database processing is finished, Veeam Agent creates a transactionally consistent backup of all databases running on DAG servers. The backup will include all database files from all servers included into backup scope regardless of the database processing success.

|  |
| --- |
| NOTE |
| Consider the following:   * The Exchange VSS Writer cannot create a VSS snapshot of all databases at once. That is why Veeam Agent backs up DAG servers one by one.  * Veeam Agent backs up all active and passive copies of the database on all DAG servers. Otherwise, Veeam Agent will not be able to ensure data consistency as Microsoft Exchange transfers data from active copy to passive copies after some time. |

1. Veeam Agent notifies the Exchange VSS Writer about successful backup. If required, the Exchange VSS Writer truncates logs on DAG servers.

Log truncation is applied to all passive and active database copies. Veeam Agent uses the Exchange VSS Writer to truncate logs. However, you can set Veeam Agent to disable transaction logs or backup transaction logs with Veeam Agent in the backup job settings. To learn more, see [Guest Processing Settings](agent_job_vss.md).

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
