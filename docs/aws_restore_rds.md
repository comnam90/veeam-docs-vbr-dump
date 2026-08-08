---
title: "Restoring RDS Instances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring RDS Instances


You can recover corrupted DB instances and Aurora DB clusters in the backup appliance Web UI only. However, you can launch the RDS Restore wizard directly from the Veeam Backup & Replication console to start the restore operation:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Backups > Snapshots.
3. Expand the backup policy that protects a resource you want to recover and do the following:

1. If you want to restore a DB instance, select the necessary instance and click Amazon RDS on the ribbon.
2. If you want to restore a Aurora DB cluster, select the necessary cluster and click Amazon RDS cluster on the ribbon.

Alternatively, you can right-click the selected resource and click Restore to Amazon RDS or Amazon RDS cluster.

Veeam Backup & Replication will open the RDS Restore wizard in a web browser. Complete the wizard as described in section [RDS Restore Using Web UI](aws_restore_rds_point.md).

[![Restore to Amazon RDS](images/aws_restore_rds.webp)](images/aws_restore_rds.webp "Restore to Amazon RDS")

Page updated 2026-07-20

