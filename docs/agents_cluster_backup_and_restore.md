---
title: "Backup and Restore of Failover Clusters"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_cluster_backup_and_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup and Restore of Failover Clusters


To process a failover cluster with Veeam Agent for Microsoft Windows, you must complete the following tasks:

1. In Veeam Backup & Replication, create a protection group that includes Active Directory objects and add to this protection group one of the following types of objects:

* Failover cluster account of the failover cluster whose data you want to back up
* Active Directory container that includes this failover cluster account

To learn more, see [Creating Protection Groups](protection_group_add.md).

1. In Veeam Backup & Replication, configure a Veeam Agent backup job for a failover cluster. To add a failover cluster to the backup job, do the following:

1. At the Job Mode step of the New Agent Backup Job wizard, select Failover cluster.
2. At the Computers step of the wizard, add to the job the failover cluster account that you added to a protection group at the step 1. Alternatively, you can add to the job a container or protection group that includes this failover cluster account.

To learn more, see [Creating Job for Windows Computers](agent_job_create_win.md).

|  |
| --- |
| IMPORTANT |
| You cannot create per-machine backup files with a Veeam Agent backup job that processes failover clusters because of failover cluster limitations. The backup job with failover clusters in the backup scope creates a separate backup file for each failover cluster. |

Data Restore from Failover Cluster Backups

You can perform data restore tasks with failover cluster backups created by Veeam Agent. For example, you can restore entire volumes or individual folders and files from such backups.

Consider the following:

* When you restore data of a failover cluster, make sure that the failover cluster is added to the Veeam Backup & Replication inventory as part of a protection group.
* When you restore data of a failover cluster with shared disks, Veeam Agent does not restore data of a disk witness. During volume restore for shared disks of a failover cluster, the disk witness is not displayed at the Disk Mapping step of the Volume Restore wizard.

Backup Copy from Failover Cluster Backups

You can perform data copy tasks with failover cluster backups created by Veeam Agent to a secondary location.

When you copy failover cluster backups, consider the following:

* The backup copy job creates a single backup copy file for each failover cluster.

To learn more about backup copy, see [Backup Copy](backup_copy.md).

Page updated 2026-07-22

