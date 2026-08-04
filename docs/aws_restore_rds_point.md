---
title: "Step 2. Select Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_rds_point.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Select Restore Point


At the Instances step of the wizard, you can add DB instances and Aurora DB clusters to the restore session and select restore points to be used to perform restore for each added RDS resource. By default, the backup appliance uses the most recent valid restore point. However, you can restore an RDS resource to an earlier state.

To select a restore point, do the following:

1. Select the DB instance or Aurora DB cluster, and click Restore Point.
2. In the Choose restore point window, select the necessary restore point and click Apply.

To help you choose a restore point, the backup appliance provides the following information on each available restore point:

* Date — the date when the restore point was created.
* Type — the type of the restore point:

* Snapshot — a cloud-native snapshot created by a backup policy.
* Replica — a snapshot replica created by a backup policy.
* Manual Snapshot — a cloud-native snapshot created manually.

* Restore Point Region — the AWS Region where the restore point is stored.

[![Restoring RDS Resources](images/aws_rds_restore_point.webp)](images/aws_rds_restore_point.webp "Restoring RDS Resources")

Page updated 2026-05-22

