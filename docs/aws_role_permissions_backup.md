---
title: "Backup IAM Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_role_permissions_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup IAM Permissions


To allow backup appliances to perform backup of AWS resources, IAM roles specified for backup operations must be granted specific permissions that depend on the type of AWS resources being backed up:

* [EC2 Backup IAM Role Permissions](aws_role_permissions_backup_ec2.md)
* [RDS Backup IAM Role Permissions](aws_role_permissions_backup_rds.md)
* [DynamoDB Backup IAM Role Permissions](aws_role_permissions_backup_dynamo.md)
* [Redshift Cluster Backup IAM Role Permissions](aws_role_permissions_backup_redshift.md)
* [Redshift Serverless Backup IAM Role Permissions](aws_role_permissions_backup_redshift_serverless.md)
* [EFS Backup IAM Role Permissions](aws_role_permissions_backup_efs.md)
* [FSx Backup IAM Role Permissions](aws_role_permissions_backup_fsx.md)
* [VPC Configuration Backup IAM Role Permissions](aws_role_permissions_backup_vpc.md)

Page updated 2026-05-19

