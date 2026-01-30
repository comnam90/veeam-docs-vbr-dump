---
title: "Dell Data Domain Supported Features"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/dell_dd_supported_features.html"
last_updated: "3/31/2025"
product_version: "13.0.1.1071"
---

# Dell Data Domain Supported Features


The DD Boost technology offers a set of features for advanced data processing. Veeam Backup & Replication supports the following features:

* [Distributed Segment Processing](#segment)
* [Advanced Load Balancing and Link Failover](#link)
* [Virtual Synthetics](#synthetics)
* [In-Flight Data Encryption](#encryption)
* [Per Storage Unit Streams](#unit)
* [Retention Lock](#unit)

|  |
| --- |
| Note |
| You cannot configure Managed File Replication using Veeam Backup & Replication. However, you can import and map backups replicated between Data Domain storage systems to backup, backup copy or replication jobs, or perform restore operations from such backups. |

Distributed Segment Processing

Distributed Segment Processing lets Dell Data Domain "distribute" the deduplication process and perform a part of data deduplication operations on the gateway server side.

Without Distributed Segment Processing, Dell Data Domain performs deduplication on the Dell Data Domain storage system. The gateway server sends unfiltered data blocks to Dell Data Domain over the network. Data segmentation, filtering and compression operations are performed on the target side, before data is written to disk.

With Distributed Segment Processing, operations on data segmentation, filtering and compression are performed on the gateway server side. The gateway server sends only unique data blocks to Dell Data Domain. As a result, the load on the network reduces and the network throughput improves.

Advanced Load Balancing and Link Failover

Advanced Load Balancing and Link Failover allow you to balance data transfer load and route VM data traffic to a working link in case of network outage problems.

Without Advanced Load Balancing, every gateway server connects to Data Domain on a dedicated Ethernet link. Such configuration does not provide an ability to balance the data transfer load across the links. If a network error occurs during the data transfer process, the backup job fails and needs to be restarted.

Advanced Load Balancing allows you to aggregate several Ethernet links into one interface group. As a result, Dell Data Domain automatically balances the traffic load coming from several gateway servers united in one group. If some link in the group goes down, Dell Data Domain automatically performs link failover, and the backup traffic is routed to a working link.

Virtual Synthetics

Veeam Backup & Replication supports Virtual Synthetic Fulls by Dell Data Domain. Virtual Synthetic Fulls let you synthesize a full backup on the target backup storage without physically copying data from source datastores or volumes. To construct a full backup file, Dell Data Domain uses pointers to existing data segments on the target backup storage. Virtual Synthetic Fulls reduce the workload on the network and backup infrastructure components and increase the backup job performance.

In-Flight Data Encryption

Veeam Backup & Replication supports in-flight encryption introduced in Dell Data Domain Boost 3.0. If necessary, you can enable data encryption at the backup repository level. Veeam Backup & Replication will leverage the Dell Data Domain technology to encrypt data transported between the DD Boost library and Data Domain system.

Per Storage Unit Streams

Veeam Backup & Replication supports per storage unit streams on Dell Data Domain. The maximum number of parallel tasks that can be targeted at the backup repository (the Limit maximum concurrent tasks to N setting) is applied to the storage unit, not the whole Dell Data Domain system.

Retention Lock

Together with Data Domain Retention Lock, Veeam Backup & Replication allows you to prohibit deletion of data from the Dell Data Domain deduplicating storage appliances by making that data temporarily immutable. This is required for improved security: immutability protects your data from loss as a result of malware activity or unplanned actions.

You can enable the immutability feature and specify the immutable period when adding or editing the Dell Data Domain backup repository. For more information, see [Configure Backup Repository Settings](dsa_repository_repository.md). Once imposed, immutability prohibits deletion of data from the deduplicating storage appliance until the immutability expiration date comes. Note that if you enable immutability and Veeam Backup & Replication does not start a new backup chain and still continues the chain, the whole backup chain is marked as immutable. Once you disable immutability, newly created backups are not marked as immutable.

In many respects, Dell Data Domain with enabled immutability works similarly to the hardened repository. For more information on how repositories with immutability operate as a part of a scale-out backup repository, see [Hardened Repository as Performance Extent](hardened_repository_about.md#sobr). For more information on how retention periods set in jobs correlate with retention periods set in the deduplicating storage appliance, see [Retention Scenarios](hardened_repository_about.md#retention).

Related Topics

* [Dell Data Domain](dell_dd.md)
* [Accelerated Restore of Entire VM](dell_dd_accelerated_restore.md)
* [Adding Deduplicating Storage Appliances](dsa_repository_add.md)


