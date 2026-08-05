---
title: "RDS Snapshot Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_retention_snapshots_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# RDS Snapshot Retention


For cloud-native snapshots and snapshot replicas, the backup appliance retains the number of latest restore points defined in backup scheduling settings.

During every successful backup session, the backup appliance creates a new restore point. If the backup appliance detects that the number of restore points in the snapshot chain exceeds the retention limit, the earliest restore point is removed from the chain. For more information on the snapshot deletion process, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_DeleteSnapshot.html).

[![EC2 Snapshot Retention](images/aws_snapshot_retention.webp)](images/aws_snapshot_retention.webp "EC2 Snapshot Retention")

|  |
| --- |
| Note |
| Backup appliances do not apply retention policy to cloud-native snapshots created manually. To learn how to remove them, see [Managing Backed-Up Data](aws_snapshots_remove_individual_rds.md). |

Page updated 2026-05-15

