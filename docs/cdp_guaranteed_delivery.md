---
title: "Guaranteed Delivery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_guaranteed_delivery.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Guaranteed Delivery


In CDP, data delivery between any two backup infrastructure components is guaranteed by means of the TCP protocol. However, there can be situations when Veeam Backup & Replication is not able to send all data changes generated during CDP in time. For example, if RPO is small, a VM generates a lot of changes, but the infrastructure performance is not enough; or a CDP proxy gets out of work because of a power outage, and all data changes stored on it are lost. This makes data inconsistent and leads to the loss of restore points.

Site-Specific Procedures

CDP has a special mechanism and tools that return data into the consistent state. The I/O filter on the source host has a mechanism that tracks data blocks that have changed — change tracking (CT). For more information, see [Change Tracking](#ct). Additionally, CDP proxies store data changes until a confirmation message that blocks are saved is received from the target host.

How Veeam Backup & Replication uses these tools depend on whether issues occur on the source or target site:

* Source site. If the source host does not send the data changes because of the high system load, Veeam Backup & Replication activates the change tracking (CT) mechanism. Until all the changed data blocks are saved to the target, the data remains inconsistent. As a result, there are "gaps" in the restore point journal and you are not able to restore a VM to some points in time. However, after the target host saves the data, the CDP policy resumes the creation of consistent restore points.

If the source proxy gets out of work, Veeam Backup & Replication selects another CDP proxy and then behaves as described in the previous paragraph, except for waiting for the load decrease.

* Target site. If the target proxy gets out of work, Veeam Backup & Replication selects another CDP proxy and requests data changes from the source CDP proxy. The proxy sends the changes to the target host once again, and the data on the target host becomes consistent almost immediately, so that you are able to restore a VM to any point in time.

If the connection between the target CDP proxy and the target host is lost, Veeam Backup & Replication checks the host state. If the host is in the Maintenance mode or has disappeared from the cluster, Veeam Backup & Replication starts writing data changes to replicas using another target ESXi host (provided that the host exists and is connected to the datastore where replicas are stored). If the host is not in the Maintenance mode or has not disappeared, Veeam Backup & Replication considers that these are temporary problems with the network and sends data changes again after some time.

Change Tracking

To ensure consistent data delivery and reliable restore points, CDP uses its proprietary change tracking (CT) mechanism. The CT mechanism is activated during the initial synchronization and whenever issues with data transfer occur.

At the core of the CT mechanism, there are two processes:

* Construction of the dirty block map
* Continuous sending of dirty blocks to the target

The dirty block map is an internal bitwise structure for tracking disk changes. This map divides each protected disk into blocks and marks blocks as "dirty" when changes occur. When a block is sent to the target, it is marked as "clean". Veeam Backup & Replication tracks the delivery status of blocks sent to the target host. Once the target host confirms successful receipt of blocks, the source host stops tracking the delivery status of this block until new changes occur. If the confirmation is not received, Veeam Backup & Replication resends the blocks.

Veeam Backup & Replication attempts to send the dirty blocks to the target (synchronize blocks) as quickly as allowed by the infrastructure and network conditions. If the transfer channel is blocked or infrastructure performance is insufficient, some blocks may remain dirty longer. Additionally, blocks that were previously clean can become dirty again if new changes occur. As a result, the total number of synchronized blocks does not always increase monotonously. Under heavy system load, the proportion of clean blocks may temporarily decrease as new changes accumulate faster than they can be synchronized.

CT during Initial Synchronization

At the beginning of the initial synchronization, all blocks are marked as dirty. The system iteratively reads each dirty block, transfers its data to the target, and marks it as clean. This process continues until all blocks are clean, signifying that the disk state is fully replicated.


