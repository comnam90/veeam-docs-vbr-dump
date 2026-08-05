---
title: "Step 2. Select Databases"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_rds_database_point.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Select Databases


At the Databases step of the wizard, you can add databases to the restore session and select a restore point that will be used to perform the restore operation for each database. By default, the backup appliance uses the most recent valid restore point. However, you can restore the database data to an earlier state.

To help you choose a restore point, the backup appliance provides the following information on each available restore point:

* Date — the date when the restore point was created.
* Type — the type of the restore point:

* Backup — an image-level backup created by a backup policy.
* Archive — an archived backup created by a backup policy.

* State — the state of the restore point stored in the standard backup repository:

* Healthy — the restore point has been verified by the health check session and reported to be healthy.
* Incomplete — the restore point has been verified by the health check session and reported to be corrupted or incomplete.

* Storage Class— the storage class of the backup repository where the restore point is stored.
* Restore Point Region — the AWS Region where the restore point is stored.

|  |
| --- |
| Important |
| For Microsoft SQL Server DB instances, Veeam Plug-in for AWS does not support restoring databases that contain the FILESTREAM file group. |

[![Restoring RDS Databases](images/aws_rds_restore_database_point.webp)](images/aws_rds_restore_database_point.webp "Restoring RDS Databases")

Page updated 2026-05-22

