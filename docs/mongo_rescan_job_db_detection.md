---
title: "Backup Source Selection"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_rescan_job_db_detection.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# Backup Source Selection


During the application backup policy run, Veeam Mongo Agent running on the target computer collects information about databases included in MongoDB replica sets that were processed during the previous [rescan job](mongo_rescan_job.md). Using this information, Veeam Backup & Replication selects a node in a replica set that will be a backup source for the backup session.

On the target computer, Veeam Backup & Replication and Veeam Mongo Agent collect information about MongoDB in the following way:

1. Veeam Backup & Replication connects to each replica set node that was added to the backup scope during [the protection group configuration](mongo_protection_group_scope_computers.md).
2. Veeam Backup & Replication collects the following node details: topology, health, version. If necessary, Veeam Backup & Replication also updates mongod and configuration database on the nodes.
3. Veeam Backup & Replication selects a node that will be a backup source. By default, Veeam Backup & Replication selects the node automatically in the following way:

* If there is a previous backup in a backup chain and the previously selected node is healthy, Veeam Backup & Replication uses this node as a backup source again.

If the previously selected node is primary, Veeam Backup & Replication will display a warning and continue to run the job.

* If there is no previous backups in a backup chain or the previously selected node cannot be selected, Veeam Backup & Replication selects the node from the replica set as follows:

1. Excludes arbiter nodes.
2. Excludes unhealthy and unreachable nodes.
3. Excludes hidden nodes.
4. From the nodes that are not excluded, Veeam Backup & Replication selects a secondary node with a call back delay below 30 seconds.
5. If the node is not selected during the previous steps and you allowed Veeam Backup & Replication [to back up from primary nodes](mongo_policy_preferences_processing.md), primary nodes are selected.
6. If several nodes are selected, Veeam Backup & Replication select nodes with the lowest priority from the set.
7. If several nodes are still selected, Veeam Backup & Replication removes voting nodes. If all selected nodes are voting, Veeam Backup & Replication does not remove any nodes.
8. If several nodes are still selected, Veeam Backup & Replication sorts nodes in the ascending order by MemberId and selects the first node in the list.

This step does not consider any performance details of a node. It allows Veeam Backup & Replication to select the node in any configuration.

According to the described logic, Veeam Backup & Replication selects a backup source for each replica set included in a backup scope.

|  |
| --- |
| Note |
| The user can alter the default way Veeam Mongo Agent selects the backup source. For example, the user can configure Veeam Mongo Agent to use the primary node as a backup source. For more information, see [Specify Backup Preferences](mongo_policy_preferences.md). |

After the backup source is selected, Veeam Backup & Replication continues the backup operation. For details, [Application Backup Policies](mongo_backup_job.md#3).


