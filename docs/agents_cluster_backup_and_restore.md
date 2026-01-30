---
title: "Backup and Restore of Failover Clusters"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_cluster_backup_and_restore.html"
last_updated: "12/4/2025"
product_version: "13.0.1.1071"
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
| * If a backup task within a Veeam Agent backup job that processes a failover cluster completes unsuccessfully or a new node is added to a failover cluster, Veeam Agent will create a full backup of all shared disks of the failover cluster during the next backup job run. * You cannot create per-machine backup files with a Veeam Agent backup job that processes failover clusters because of failover cluster limitations. The backup job with failover clusters in the backup scope creates a separate backup file for each failover cluster. |

Data Restore from Failover Cluster Backups

You can perform data restore tasks with failover cluster backups created by Veeam Agent. For example, you can restore entire volumes or individual folders and files from such backups.

Consider the following:

* When you restore data of a failover cluster, make sure that the failover cluster is added to the Veeam Backup & Replication inventory as part of a protection group.
* When you restore data of a failover cluster with shared disks, Veeam Agent does not restore data of a disk witness. During volume restore for shared disks of a failover cluster, the disk witness is not displayed at the Disk Mapping step of the Volume Restore wizard.

Backup Copy from Failover Cluster Backups

You can perform data copy tasks with failover cluster backups created by Veeam Agent to a secondary location.

When you copy failover cluster backups, consider the following:

* The backup copy job creates a single backup copy file for each failover cluster.

* When you copy Veeam Agent backup jobs that process failover clusters with shared disks, the network traffic is higher compared to the traffic sent when Veeam Agent backup jobs run. This happens because Veeam Agent backup copy jobs send data as it is stored in the storage — each node with the cloned data — unlike Veeam Agent backup jobs that send data of shared disks only with the owner node and then, within the target storage, clone this data to other nodes.

* Data deduplication is not available when you copy Veeam Agent backup jobs that process failover clusters with shared disks to an object storage repository.

|  |
| --- |
| IMPORTANT |
| In this case, you may require additional free space on the target location, because Veeam Backup & Replication creates in the target location as many copies of the cluster shared disks as there are nodes in the cluster. |

To learn more about backup copy, see [Backup Copy](backup_copy.md).


