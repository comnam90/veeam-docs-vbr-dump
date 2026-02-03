---
title: "Specifying Microsoft SQL Server Transaction Log Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_job_create_gp_mssql.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Specifying Microsoft SQL Server Transaction Log Settings


By default, Veeam Backup & Replication creates application-consistent image-level backups of VMs running the Microsoft SQL Server application and truncates transaction logs after each successfully completed backup session — this will allows you to restore Microsoft SQL Server databases using specific backups. To protect mission-critical Microsoft SQL Server databases, you can instruct Veeam Backup & Replication to create secondary restore points with transaction logs in addition to primary image-level backups — this will allow you to restore your databases to [specific points in time](https://helpcenter.veeam.com/docs/vbr/explorers/vesql_restoring_pit.html?ver=13).

|  |
| --- |
| NoteS |
| * Veeam Backup & Replication stores image-level backups and transaction log backups in the same repository. * If Veeam Backup & Replication fails to produce a primary image-level backup, no secondary transaction log backups will be created. |

To back up Microsoft SQL Server transaction logs periodically, do the following:

1. Switch to the SQL tab and select the Backup logs periodically option.
2. In the Backup logs every field, specify how frequently you want transaction logs to be backed up. The maximum field value is 480 minutes.
3. In the Retain log backups section, choose either of the following options:

* Select the Until the corresponding image-level backup is deleted option if you want to remove transaction log backups and the related image-level backups at the same time, according to the retention policy settings specified at [step 4](pve_backup_job_create_destination.md).

* Select the Keep only last <N> days of log backups option if you want to retain transaction logs for a specific time period, regardless of the retention policy settings specified for image-level backups. Note that image-level backups must always be kept for a longer period than the related transaction log backups.

For more information on how Veeam Backup & Replication retains transaction logs, see [Microsoft SQL Server Log Backup](sql_backup_retention.md).

1. In the Log shipping servers section, choose whether you want to use a specific Windows server to transfer transaction log backups or let Veeam Backup & Replication choose it automatically to reduce the load on the backup server.

By default, Veeam Backup & Replication automatically chooses a log shipping server for each of the processed VMs based on network settings and rules listed in section [Log Shipping Servers](sql_backup_log_shipping.md). You can also manually limit the list of machines that may be used as log shipping servers — to do that, click Choose, select the Use the specified servers only option and then select check boxes next to the necessary Windows servers.

For a Windows server to be displayed in the list of available log shipping servers, it must be added to the backup infrastructure as described in section [Adding Microsoft Windows Servers](add_windows_server.md). Keep in mind that the list will also include Linux servers added to the backup infrastructure; however, Linux servers cannot be used as log shipping servers due to technical limitations in the current version.

|  |
| --- |
| TipS |
| * It is recommended that you choose at least 2 log shipping servers for load balancing and high availability purposes. * It is recommended that you do not choose servers that are engaged in permanent tasks consuming resources (such as WAN accelerators or backup servers). |

You can also choose not to truncate logs at all. However, keep in mind that this option requires databases to use the simple recovery model. Otherwise, transaction logs may grow large and increase the storage space consumption significantly. For more information on recovery models used by Microsoft SQL databases, see [Microsoft Docs](https://learn.microsoft.com/en-us/sql/relational-databases/backup-restore/recovery-models-sql-server?view=sql-server-ver16).

Considerations and Limitations

When you configure transaction log settings, consider the following:

* If a processed VM runs Microsoft SQL Server as part of a Windows Server Failover Cluster, Veeam Backup & Replication will not be able to create an application-consistent backup — an image-level backup will be created instead. To work around the limitation, [use Veeam Agent](agents_cluster_support.md) managed by Veeam Backup & Replication.

* If a processed VM runs Microsoft SQL Server along with Oracle Server and transaction log backup is enabled for both applications, the Microsoft SQL Server transaction logs will not be backed up — Veeam Backup & Replication will create transaction log backups for the Oracle Server application only.

* If a processed VM runs Microsoft SQL Server that hosts the Veeam Backup & Replication configuration database, its transaction logs will not be backed up:

* If the Microsoft SQL Server has the SQL Server Always On availability groups feature disabled, the configuration database will be excluded from application-aware processing automatically.
* If the Microsoft SQL Server has the SQL Server Always On availability groups feature enabled, you will have to exclude the configuration database from application-aware processing manually, as described in [this Veeam KB article](https://www.veeam.com/kb2110).

For more information on the SQL Server Always On availability group feature, see [Microsoft Docs](https://learn.microsoft.com/en-us/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server?view=sql-server-ver16).

![Microsoft SQL Server Transaction Log Settings](images/pve_backup_job_create_gp_mssql.webp)


