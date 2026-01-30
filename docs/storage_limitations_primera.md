---
title: "HPE Alletra Storage MP B10000, 9000, Primera, 3PAR"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_limitations_primera.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---

# HPE Alletra Storage MP B10000, 9000, Primera, 3PAR


If you plan to perform operations with HPE Alletra Storage MP B10000, 9000, Primera, 3PAR storage systems, consider the following:

* If a volume has exports to an NVMe host, rescan of this volume may fail. To avoid failures, remove the volume from the rescan scope as described in [Limiting Rescan Scope](storage_rescan.md#limit_rescan).

* Virtual Domains are supported.
* [For HPE 3PAR Peer Persistence] [Failover to Backup from Storage Snapshots](storage_secondary_backup.md#failover) on the primary storage array is not supported.
* The following applies to the immutability feature:

* Make sure that the license on the storage system supports HPE Virtual Lock and that the VVRetentionTimeMax parameter is specified.
* If you change the immutability period for a snapshot, also known as the retention time in storage system terms, by means of the storage system, the updated immutability period is shown in the Veeam Backup & Replication UI. However, this update will only appear after [rescan of the storage system](storage_discovery_process.md). In the UI, you can find the immutability period in the Storage Infrastructure view, in the Immutable Until column.
* To show snapshots created by native means of a storage system (without Veeam Backup & Replication) as immutable, make sure that they are read-only and the retention time is specified for them.

* [For HPE Alletra Storage MP B10000] The following applies to iSCSI connections:

* [For releases prior to 10.4] The proxy server initiator must be manually connected with the storage iSCSI target even though the host on the storage is created automatically.
* [For releases prior to 10.4] For data recovery, the target ESXi host initiator must be manually connected to the storage iSCSI target.
* [For releases prior to 10.4] The proxy server IQN and Veeam iSCSI IQN used for host discovery must be registered with the same host on the storage. If the service "VeeamAUX" host with Veeam IQN exists, it should be removed. For more information on the Veeam iSCSI IQN, see [Veeam iSCSI Initiator (VMware Integration)](storage_discovery_process.md).
* During the registration on the storage, the proxy server initiator IQN should be specified in lowercase, even if it is originally in uppercase.

* [For Synchronous Long Distance (SLD) remote copy configuration] If you add the synchronous replication (Remote Copy Peer Persistence) feature and the snapshot transfer (Remote Copy Periodic asynchronous) feature to the same backup job, only synchronous replication will be used.

* [For VMware and Veeam Agent integration] If storage LUNs reside in a virtual domain, the proxy to which LUNs are exported must reside in the same virtual domain. If LUNs reside outside a virtual domain, the backup proxy must also reside outside any available virtual domain.

* [For backup from storage snapshots and data recovery] Export types such as "Hosts and port" and "Port" are not supported. If you create such export types for a proxy or ESXi host, Veeam Backup & Replication will automatically create exports with the "Host" or "Host set" types instead.
* The following applies to snapshot orchestration and backup from storage snapshots with snapshot retention:

+ [Enable HPE Web Services API server](storage_configure_enable_web.md). Veeam Backup & Replication uses the HPE Web Services API server to work with the HPE Alletra Storage MP B10000, 9000, Primera, 3PAR storage system.
+ A license for the storage system must support Virtual Copy.
+ You can use backup jobs to create a snapshot chain either on a primary or on a secondary storage array, but you cannot configure snapshot creation on both storage arrays at the same time.

* [For backup from secondary storage arrays and backup with snapshot retention] For Peer Persistence and Remote Copy features, you must create a Remote Copy Group (RCG) with relevant type (Synchronous or Periodic).


