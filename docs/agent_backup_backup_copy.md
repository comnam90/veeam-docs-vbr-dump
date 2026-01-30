---
title: "Performing Backup Copy for Veeam Agent Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_backup_backup_copy.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Performing Backup Copy for Veeam Agent Backups


You can configure backup copy jobs that will copy backups created with Veeam Agent to a secondary backup repository.

Backup copy jobs treat Veeam Agent backups as usual backup files. The backup copy job setup and processing procedures practically do not differ from the same procedures for a backup copy job that processes VM backups. To learn more about backup copy jobs, see  [Backup Copy](backup_copy.md).

![Performing Backup Copy for Veeam Agent Backups](images/agents_integration_backup_copy.webp "Perform Backup Copy for Veeam Agent Backups")

Considerations and Limitations for Copying Failover Cluster Backups

When you copy failover cluster backups, consider the following:

* The backup copy job creates a single backup copy file for each failover cluster.
* When you copy Veeam Agent backup jobs that process failover clusters with shared disks, the network traffic is higher compared to the traffic sent when Veeam Agent backup jobs run. This happens because Veeam Agent backup copy jobs send data as it is stored in the storage — each node with the cloned data — unlike Veeam Agent backup jobs that send data of shared disks only with the owner node and then, within the target storage, clone this data to other nodes.

* Data deduplication is not available when you copy Veeam Agent backup jobs that process failover clusters with shared disks to an object storage repository.

|  |
| --- |
| IMPORTANT |
| In this case, you may require additional free space on the target location, because Veeam Backup & Replication creates in the target location as many copies of the cluster shared disks as there are nodes in the cluster. |

Restoring Data from Copies of Veeam Agent Backups

Backups copied to the secondary backup repository do not preserve user access permissions. At the same time, users who created backups do not have access permissions on these secondary repositories. For this reason, users cannot restore data from their backups residing in the secondary site.

To overcome this limitation, you can delegate the restore task to backup administrators who work with Veeam Backup & Replication. Backup administrators can use Veeam Backup & Replication options to recover data from such backups: for example, perform file-level restore or retrieve necessary application items with Veeam Explorers.

You can also restore data from the copied backup stored in the target repository using Veeam Agent.


