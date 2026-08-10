---
title: "Changed Block Tracking"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_cbt.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Changed Block Tracking


The changed block tracking (CBT) mechanism allows backup appliances to reduce the amount of data read from processed EBS volumes, and to increase the speed and efficiency of incremental backups:

* During a full backup session, the backup appliance reads only written data blocks, while unallocated data blocks are filtered out.
* During an incremental backup session, the backup appliance reads only those data blocks that have changed since the previous backup session. > During an incremental backup session, only those data blocks that have changed since the previous backup session are read.

To detect unallocated and changed data blocks, CBT relies on [EBS Direct APIs](https://docs.aws.amazon.com/ebs/latest/APIReference/Welcome.html).

1. During the first (full) backup session, the backup appliance [creates a cloud-native snapshot](aws_backup_hiw_ec2.md#step1) of an EC2 instance. To do that, the backup appliance sends API requests to access the content of the snapshot and to detect unallocated data blocks.
2. During subsequent sessions, new cloud-native snapshots are created. The backup appliance sends API requests to access and to compare the content of the snapshot created during the previous backup session and the snapshot created during the current backup session. This allows the backup appliance to detect data blocks that have changed since the previous backup session.

|  |
| --- |
| Note |
| The CBT mechanism is optional for SLA-based backup policies. However, to increase the speed and efficiency of incremental backups, it is recommended that you enable CBT in SLA templates. For more information, see [CBT Impact on Snapshot Retention](aws_cbt_retention.md). |

Limitations for Changed Block Tracking

Backup appliances cannot use CBT for EC2 instances that reside in AWS Regions where EBS Direct APIs are not available.

If CBT cannot be used, backup appliances read the whole content of processed EBS volumes and compares it with backed-up data that already exists in the backup repository. In this case, it may take backup appliances more time to create incremental backups.

Related Topics

[CBT Impact on Snapshot Retention](aws_cbt_retention.md)

Page updated 2026-05-15

