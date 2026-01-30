---
title: "Backup of Always On Availability Groups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_cluster_always_on_hiw.html"
last_updated: "8/5/2025"
product_version: "13.0.1.1071"
---

# Backup of Always On Availability Groups


To process Always On Availability Group, you must complete the following tasks:

1. In Veeam Backup & Replication, create a protection group that includes Active Directory objects. Add to this protection group the failover cluster account of the failover cluster whose data you want to back up.
2. In Veeam Backup & Replication, configure a Veeam Agent backup job for a failover cluster. To add a failover cluster to the backup job, do the following:

1. At the Job Mode step of the New Agent Backup Job wizard, select Failover cluster.
2. At the Computers step of the wizard, add to the job the failover cluster account that you added to a protection group at the step 1. Alternatively, you can add to the job a container or protection group that includes this failover cluster account.
3. At the Guest Processing step of the wizard, select the Enable application-aware processing option. Then click Applications. In the Processing Settings window, define processing settings. To learn more, see [Application-Aware Processing](agent_job_vss_general.md).

To learn more about the backup job configuration, see [Creating Job for Windows Computers](agent_job_create_win.md).

If you select to process transaction logs with the backup job in the Processing Settings window, Veeam Backup & Replication performs the following operations during an image-level backup:

1. Requests and analyzes information about databases that are included in the Always On Availability Groups.
2. Depending on the retrieved information, selects the VSS backup type for each computer: full backup (VSS\_BT\_FULL) or copy-only backup (VSS\_BT\_COPY). The copy-only backup is created if the computer represents a secondary node for at least one Always On Availability Group.

To learn more about VSS backup types, see [Microsoft documentation](https://docs.microsoft.com/en-us/windows/win32/api/vss/ne-vss-vss_backup_type).

Transaction Log Backup

You can enable transaction log backup in the Processing Settings window. To learn more, see [Microsoft SQL Server Transaction Log Settings](agent_job_vss_sql.md).

Transaction log backup can be performed only for those databases that were successfully backed up, on the primary or on the secondary node of Always On Availability Group. At each log processing interval, Veeam Backup & Replication chooses the Always On Availability Group node for which transaction logs will be backed up. Logs are backed up from one node of the Always On Availability Group.

To become a subject for a log backup, the node must meet the following criteria:

* The node is not subject to the limitations listed in section [Failover Cluster Support](agents_cluster_support.md).
* The necessary Veeam Backup & Replication components must be installed on this node and the computer included in Always On Availability Group must be running. For more information on the necessary components, see [How Microsoft SQL Server Log Backup Works](sql_backup_hiw.md).
* The database backup preferences settings must allow a backup of the node that you want to process. For example, if you want to back up the primary node, you must not exclude this node from a backup, or select the Secondary only option in the database backup preferences settings.
* Databases in the Always On Availability Groups for this node were successfully backed up for the last two processing intervals.


