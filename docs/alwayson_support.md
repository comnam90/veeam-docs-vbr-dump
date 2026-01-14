---
title: "Support for Always On Availability Groups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/alwayson_support.html"
last_updated: "12/17/2025"
product_version: "13.0.1.1071"
---

# Support for Always On Availability Groups

In this article

Always On Availability Groups allow you to increase fault tolerance between active and hot-standby databases without involving shared physical disks, which is quite important for the virtualization of Microsoft SQL Servers. Veeam Backup & Replication supports Always On Availability Groups for virtualized Microsoft SQL Server 2012 or later.

Veeam Backup & Replication supports the following Always On Availability Groups:

* Always On Availability Groups based on the Windows Server Failover Cluster (WSFC)
* Always On Clusterless Availability Groups

Veeam Backup & Replication does not support Always On Availability Groups based on SQL Server Failover Cluster Instances (FCIs).

Image-level Backup of Microsoft SQL Server VMs

During an image-level backup of a Microsoft SQL Server VM, Veeam Backup & Replication requests and analyzes information about databases that are included in the Always On Availability Groups. Depending on the retrieved information, Veeam Backup & Replication creates a VSS snapshot with or without COPY\_ONLY flag. The VSS\_BS\_COPY flag for VSS snapshot is triggered if the VM represents a secondary node for at least one Always On Availability Group.

Veeam Backup & Replication also detects to what cluster the database belongs. If the backup job does not include all VMs from the cluster, an information message will be issued.

Retrieved information is saved for further log identification.

Transaction Log Backup

Transaction log backup can be performed only for those databases that were successfully backed up, either on the primary or on the secondary node of Always On Availability Group.

The transaction logs processing interval may be the same or may differ through VMs included in Always On Availability Group. If the interval is different, Veeam Backup & Replication will use a minimal value (by default, 15 minutes).

At each log processing interval, Veeam Backup & Replication chooses the Always On Availability Group node for which transaction logs will be backed up.

Logs are backed up from one node of the Always On Availability Group. To become a subject for a log backup, the node must meet the following criteria:

* The necessary Veeam Backup & Replication components must be installed on this node and the VM included in Always On Availability Group must be running. For more information on the necessary components, see [How Microsoft SQL Server Log Backup Works](sql_backup_hiw.md).
* The database backup preferences settings must allow a backup of the node you want to process. For example, if you want to back up the primary node, you must not exclude this node from a backup, or select the Secondary only option in the database backup preferences settings.
* Databases in the Always On Availability Groups for this node were successfully backed up for the last two processing intervals.
* Veeam Backup & Replication can establish a network connection to the node or VIX connection if a connection over the network cannot be established.

|  |
| --- |
| Note |
| When you configure a backup job to process Distributed Availability Groups transaction logs, select either primary or secondary distributed availability group. Otherwise, the log chain of the distributed group databases may become inconsistent.  When you configure a backup job to back up transaction logs for other Distributed Availability Groups, use the Perform copy only mode. See [Application-Aware Processing](backup_job_vss_application_vm.md) to learn more about the copy only mode. You can also use the exclude feature to prevent Guest-OS database from being processed. See [Exclude Objects from Backup Job](backup_job_excludes_vm.md) to learn more on excluding objects. To read about distributed availability group limitations, see [Configure distributed availability group](https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/configure-distributed-availability-groups). |

Page updated 12/17/2025

Page content applies to build 13.0.1.1071
