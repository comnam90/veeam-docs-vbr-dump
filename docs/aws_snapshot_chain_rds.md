---
title: "Snapshot Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_snapshot_chain_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Snapshot Chain


During every backup session, the backup appliance creates a cloud-native snapshot for each instance added to the backup policy. The cloud-native snapshot is taken using native AWS capabilities.

A sequence of cloud-native snapshots created during a set of backup sessions makes up a snapshot chain. The backup appliance creates the snapshot chain in the following way:

1. During the first backup session, the backup appliance creates a snapshot that contains all instance data and saves it in the AWS Region where the processed instance resides. This snapshot becomes a starting point in the snapshot chain.

The creation of the first snapshot may take significant time to complete since the backup appliance copies the whole image of the instance.

1. During subsequent backup sessions, the backup appliance creates snapshots that contain only those data blocks that have changed since the previous backup session.

The creation of subsequent snapshots typically takes less time to complete, compared to the first snapshot in the chain. Note, however, that the completion time still depends on the amount of data being processed.

For more information on how incremental snapshots work, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ManagingManualBackups.html).

Each cloud-native snapshot in the snapshot chain contains encrypted metadata. Metadata stores information about the protected instance and the backup policy that created the snapshot. The backup appliance uses metadata to identify snapshots created by the Veeam backup service, to detect outdated snapshots, to load the configuration of source instances during recovery operations, and so on.

Cloud-native snapshots act as independent restore points for backed-up instances. If you remove any snapshot, it will not break the snapshot chain — you will still be able to roll back instance data to any existing restore point.

[![Snapshot Chain](images/aws_rds_snapshot_chain.webp)](images/aws_rds_snapshot_chain.webp "Snapshot Chain")

The number of cloud-native snapshots kept in a snapshot chain is defined by retention policy settings. For more information, see [RDS Snapshot Retention](aws_retention_snapshots_rds.md).

|  |
| --- |
| Note |
| Cloud-native snapshots created manually are not included into the snapshot chain. Therefore, these snapshots are not removed automatically according to retention policy settings. For information on how to remove them, see [Managing Backed-Up Data](aws_snapshots_remove_individual_rds.md). |

Snapshot Replica Chain

Snapshot replicas are copies of cloud-native snapshots that backup appliances creates during backup sessions. If you enable snapshot replication for a backup policy, the backup appliance will make a copy of the initially created cloud-native snapshot and save it to the target AWS Region in the target AWS account specified in backup policy settings. Snapshot replicas created in the target AWS Region during a set of backup sessions make up a snapshot replica chain.

The backup appliance creates and maintains the snapshot replica chain in the same way as the regular snapshot chain:

* The first snapshot replica of the processed instance becomes a starting point in the snapshot replica chain.
* Snapshot replicas created during subsequent backup sessions store only those data blocks that have changed since the previous backup session.

Related Topics

[RDS Snapshot Retention](aws_retention_snapshots_rds.md)

Page updated 2026-05-15

