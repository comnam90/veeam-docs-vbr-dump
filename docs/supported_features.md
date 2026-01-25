---
title: "Supported Storage Features for Backup and Orchestration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/supported_features.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Supported Storage Features for Backup and Orchestration


Veeam Backup & Replication supports the following native storage features for backup from storage snapshots and snapshot orchestration:

* Secondary storage array replication features. The replication features of secondary storage arrays help reduce impact on the production storage and increase the data resilience by creating additional copies of snapshots. During backup, data is read from the secondary storage array, leaving the primary storage array unaffected. Veeam Backup & Replication supports the following replication types:

* Synchronous replication.
* Snapshot transfer.

* Snapshot immutability. The snapshot immutability feature protects snapshots against unauthorized changes or deletions, which is crucial for safeguarding your data against attacks, malware, or other harmful actions. Once you enable immutability, Veeam Backup & Replication ensures that no one can delete or modify the snapshots until the immutability expiration date. In the Storage Infrastructure view, the Immutable Until column displays the immutability expiration date for each snapshot.
* Archiving snapshots. The snapshot archiving feature allows jobs to manage the offload of long-term snapshots to a 3rd-party storage solution supported by a storage vendor (for example, Amazon S3 storage or NFS target). Snapshot archiving is helpful for saving rarely accessed data. Archived snapshots are shown under the ![Supported Storage Features for Backup and Orchestration](images/icon_snapshot_archived.webp "Retrieve snaphot icon") icon.

For information on how to configure these features for different types of jobs, see [Configuring Backup from Storage Snapshots](storage_backup.md), [Configuring Backup from Snapshots on Secondary Storage Arrays](storage_secondary_backup_perform.md) and [Configuring Snapshot-Only Jobs](snapshot_only_job_perform.md).

Storage Systems and Supported Features

The following table shows which storage systems and which features supports Veeam Backup & Replication.

| Storage Type/ | Backup from Storage Snapshots | | Snapshot Orchestration / Backup from Storage Snapshots with Snapshot Retention | | Snapshot Immutability | Snapshot Archiving and Data Retrieval |
| --- | --- | --- | --- | --- | --- | --- |
| Primary Storage Arrays | Secondary Storage Arrays | Primary Storage Arrays | Secondary Storage Arrays |
| Built-in Storage Systems | | | | | | |
| Cisco HyperFlex HX-Series | ✓ | ✕ | ✕ | ✕ | ✕ | ✕ |
| Dell Unity (XT) | ✓ | ✕ | ✕ | ✕ | ✕ | ✕ |
| Fujitsu ETERNUS HX/AX, | ✓ | SnapMirror SnapVault | ✓ | SnapMirror1 SnapVault2 | ✕ | ✕ |
| HPE 3PAR StoreServ,  HPE Primera,  HPE Alletra 9000, HPE Alletra Storage MP B10000 | ✓ | Remote Copy Peer Persistence3 Remote Copy Periodic (Asynchronous) | ✓ | Remote Copy Peer Persistence1, 3 Remote Copy Periodic (Asynchronous)2 | Virtual Lock | ✕ |
| HPE Nimble Storage AF-Series,  HPE Nimble Storage HF-Series, HPE Nimble Storage CS-Series, HPE Alletra 5000, HPE Alletra 6000 | ✓ | Snapshot Replication Synchronous Replication (including Peer Persistence) | ✓ | Snapshot Replication2 Synchronous Replication (including Peer Persistence)1 | ✕ | ✕ |
| Universal Storage API Integrated Systems | | | | | | |
| DataCore SANsymphony | ✓ | ✕ | ✓ | ✕ | ✕ | ✕ |
| Dell PowerMax | ✓ | ✕ | ✓ | ✕ | ✕ | ✕ |
| Dell PowerStore | ✓ | Native Asynchronous Replication Native Metro Synchronous Replication (Metro Volume) | ✓ | Native Asynchronous Replication2 Native Metro Synchronous Replication (Metro Volume)1 | ✕ | ✕ |
| Dell SC Series (formerly Compellent) | ✓ | ✕ | ✓ | ✕ | ✕ | ✕ |
| Fujitsu ETERNUS AF and DX Series | ✓ | ✕ | ✓ | ✕ | ✕ | ✕ |
| Hitachi VSP/VSP One Block | ✓ | TrueCopy Global-Active Device (GAD) | ✓ | TrueCopy1 Global-Active Device (GAD)1 | ✓ | ✕ |
| IBM FlashSystem (formerly Spectrum Virtualize, includes IBM StorWize and IBM SVC) | ✓ | HyperSwap5 Metro Mirror5 Global Mirror4,5 | ✓ | HyperSwap1,5 Metro Mirror1,5 Global Mirror2,4,5 | ✕ | ✕ |
| INFINIDAT Infinibox F-Series | ✓ | ✕ | ✓ | ✕ | ✕ | ✕ |
| NEC Storage M Series | ✓ | ✕ | ✓ | ✕ | ✕ | ✕ |
| NetApp SolidFire/HCI | ✓ | ✕ | ✓ | ✕ | ✕ | ✕ |
| Pure Storage FlashArray | ✓ | Asynchronous Replication ActiveCluster Replication | ✓ | Asynchronous Replication2 ActiveCluster Replication1 | ✕ | Offload2 |
| Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile) | ✓ | ✕ | ✓ | ✕ | ✕ | ✕ |

1 Snapshot orchestration and backup from storage snapshots with snapshot retention requires specific licenses. For more information, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).

2 Enterprise Plus license is required.

3 For Remote Copy Peer Persistence, snapshots are created on the target volume only.

4 Global Mirror with Change Volumes is not supported.

5 For IBM Spectrum Virtualize 8.7.1 and later, the vendor no longer supports Metro Mirror, Global Mirror, and HyperSwap features. As a result, the replication feature becomes unavailable in Veeam Backup & Replication. You can configure backup and snapshot creation only for the primary storage array. For the existing backup jobs that use the replication feature, ensure the Failover to primary storage snapshot option is enabled, or remove the replication feature at the Secondary Target step of the wizard, or create new backup jobs. If you need the replication feature, use IBM Spectrum Virtualize versions prior to 8.7.1.

Secondary Storage Array Replication Features and Veeam Backup & Replication Terms

The following table shows storage systems, replication features and terms for these features in Veeam Backup & Replication.

| Storage system \ Feature term | Snapshot transfer | Synchronous replication |
| --- | --- | --- |
| Fujitsu ETERNUS HX/AX, Lenovo ThinkSystem DM/DG Series, NetApp FAS/AFF/ASA, NetApp FlexArray (V-Series), NetApp ONTAP Edge/Select/Cloud VSA | SnapMirror SnapVault | ✕ |
| HPE 3PAR StoreServ,  HPE Primera,  HPE Alletra 9000, HPE Alletra Storage MP B10000 | Remote Copy Periodic (Asynchronous) | Remote Copy Peer Persistence (Snapshots are created on the target volume only) |
| HPE Nimble Storage AF-Series,  HPE Nimble Storage HF-Series, HPE Nimble Storage CS-Series, HPE Alletra 6000,  HPE Alletra 5000 | Snapshot Replication | Synchronous Replication (including Peer Persistence) |
| IBM FlashSystem (formerly Spectrum Virtualize, includes IBM StorWize and IBM SVC) | Global Mirror (Global Mirror with Change Volumes is not supported) | HyperSwap Metro Mirror |
| Dell PowerStore | Native Asynchronous Replication | Native Metro Synchronous Replication (Metro Volume) |
| Hitachi VSP/VSP One Block | ✕ | TrueCopy Global-Active Device (GAD) |
| Pure Storage FlashArray | Asynchronous Replication | ActiveCluster Replication |


