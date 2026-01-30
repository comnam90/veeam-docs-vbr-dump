---
title: "Failover Cluster Support"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_cluster_support.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Failover Cluster Support


You can use Veeam Agent for Microsoft Windows operating in the managed mode (within the Veeam Agent management scenario) to protect data processed by a failover cluster. Veeam Agent supports Windows Server Failover Clusters running on any of the supported Microsoft Windows Server OS versions. To learn the full list of versions, see [System Requirements](agents_system_requirements.md#OSes).

Veeam Agent supports data backup and restore for the following types of failover clusters:

* Windows File Server Failover Clusters
* Windows Server Failover Clusters that run the following applications:

* Microsoft SQL Server 2012 SP4 or later
* Microsoft Exchange Server 2016 or later

Microsoft Exchange Database Availability Groups (DAGs) are supported. To learn more, see [Backup of Database Availability Groups](agents_dag_hiw.md).

Limitations for Failover Cluster Support

Failover cluster support in Veeam Agent for Microsoft Windows has the following limitations:

* Backup of failover clusters is supported in Veeam Agent managed by Veeam Backup & Replication only. You cannot process a failover cluster by Veeam Agent operating in the standalone mode.
* Backup of CSV (Cluster Shared Volumes) is not supported. Cluster disks used as CSV are automatically excluded from backup.

* Active Directory-Detached Clusters are not supported.
* Backup of Storage Replica log volumes is not supported. Such volumes are automatically excluded from backup because of Microsoft VSS limitations. To learn more, see [Microsoft documentation](https://docs.microsoft.com/en-us/windows-server/storage/storage-replica/storage-replica-known-issues#a-storage-replica-node-hangs-when-creating-snapshots).
* Backup of environments consisting of several failover clusters is not supported. For example:

* Always On Availability Groups based on SQL Server Failover Cluster Instances (FCIs). To learn more, see [Microsoft documentation](https://learn.microsoft.com/en-us/sql/database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server?view=sql-server-ver16#SQLServerFC).
* Distributed Always On Groups. To learn more, see [Microsoft documentation](https://learn.microsoft.com/en-us/sql/database-engine/availability-groups/windows/distributed-availability-groups?view=sql-server-ver16).

* Always On Availability Groups with no underlying failover cluster (Clusterless Availability Groups) are not supported.
* Backup of SQL Server failover clusters that store databases on a cluster disk is not supported if at least one of the cluster nodes hosts a local disk with the same mount point.
* SureBackup is not supported for failover clusters.

|  |
| --- |
| NOTE |
| Veeam Backup & Replication does not support simultaneous processing of Microsoft SQL Server transaction logs on SQL Server clustered instances with identical names and availability groups with identical IDs. The limitation applies to clustered instances of different failover clusters as well.  For example, you configure two backup jobs that process transaction logs of different failover clusters whose SQL clustered instances have identical names. In case these backup jobs run simultaneously, transaction logs will be processed only by the backup job that started first. The second backup job will not process transaction logs. |

In This Section

* [Backup and Restore of Failover Clusters](agents_cluster_backup_and_restore.md)
* [Backup of Database Availability Groups](agents_dag_hiw.md)
* [Backup of Always On Availability Groups](agents_cluster_always_on_hiw.md)


