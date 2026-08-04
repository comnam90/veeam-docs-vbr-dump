---
title: "Restore IAM Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restore IAM Permissions


To allow backup appliances to perform restore of AWS resources, IAM roles and IAM users whose one-time access keys are specified for restore operations must have specific permissions that depend on the type of AWS resources being restored:

* [EC2 Restore IAM Permissions](aws_role_permissions_restore_ec2.md)
* [RDS Instance Restore IAM Permissions](aws_role_permissions_restore_rds.md)
* [RDS Database Restore IAM Permissions](aws_role_permissions_restore_db.md)
* [DynamoDB Restore IAM Permissions](aws_role_permissions_restore_dynamo.md)
* [Redshift Cluster Restore IAM Permissions](aws_role_permissions_restore_redshift.md)
* [Redshift Serverless Restore IAM Permissions](aws_role_permissions_restore_redshift_serverless.md)
* [EFS Restore IAM Permissions](aws_role_permissions_restore_efs.md)
* [FSx Restore IAM Permissions](aws_role_permissions_restore_fsx.md)
* [VPC Configuration Restore IAM Permissions](aws_role_permissions_restore_vpc.md)

Page updated 2026-05-19

