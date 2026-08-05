---
title: "Step 2. Select Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_entire_point_efs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Select Restore Point


At the File System step of the wizard, you can add EFS file systems to the restore session and select restore points to be used to perform the restore operation for each added file system. By default, the backup appliance uses the most recent valid restore point. However, you can restore a file system to an earlier state.

To select a restore point, do the following:

1. Select the EFS system and click Restore Point.
2. In the Choose restore point window, select the necessary restore point and click Apply.

To help you choose a restore point, the backup appliance provides the following information on each available restore point:

* Date — the date when the restore point was created.

* Size — the size of the restore point.
* Type — the type of the restore point:

* EFS backup — an EFS backup created by a backup policy.
* EFS backup copy — a backup copy created by a backup policy.
* Manual backup — an EFS backup created manually.

* Restore Point Region — the AWS Region where the restore point is stored.

[![Restoring EFS File Systems](images/aws_restore_entire_point_efs.webp)](images/aws_restore_entire_point_efs.webp "Restoring EFS File Systems")

Page updated 2026-05-22

