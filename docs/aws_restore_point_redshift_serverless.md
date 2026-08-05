---
title: "Step 2. Select Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_point_redshift_serverless.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Select Restore Point


At the Restore Point step of the wizard, select a restore point that will be used to restore the selected Redshift Serverless namespace. By default, the backup appliance uses the most recent valid restore point. However, you can restore the namespace data to an earlier state.

To select a restore point, do the following:

1. Click Restore Point.
2. In the Choose restore point window, select the necessary restore point and click Apply.

To help you choose a restore point, the backup appliance provides the following information on each available restore point:

* Date — the date when the restore point was created.
* Type — the type of the restore point:

* Redshift Serverless backup — a Redshift Serverless backup created by a backup policy.
* Manual backup — a Redshift Serverless backup created manually.

* Restore Point Region — the AWS Region where the restore point is stored.

[![Restoring Redshift Serverless](images/aws_restore_point_redshift_serverless.webp)](images/aws_restore_point_redshift_serverless.webp "Restoring Redshift Serverless")

Page updated 2026-05-22

