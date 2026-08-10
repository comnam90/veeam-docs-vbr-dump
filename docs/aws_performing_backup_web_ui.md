---
title: "Performing Backup Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_performing_backup_web_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Backup Using Web UI


Backup appliances run backup policies for every data protection operation. A backup policy is a collection of settings that define the way backup operations are performed: what data to back up, where to store backups, when to start the backup process, and so on.

One backup policy can be used to process multiple resources within different regions, but you can back up each resource with one backup policy at a time. For example, if an instance is added to more than one backup policy, it will be processed only by a backup policy that has the highest priority. Other backup policies will skip this instance from processing. For information on how to set a priority for a backup policy, see [Setting Policy Priority](aws_policies_priority.md).

In This Section

* [Performing EC2 Backup](aws_perform_ec2_backup.md)
* [Performing RDS Backup](aws_perform_rds_backup.md)
* [Performing DynamoDB Backup](aws_perform_dynamo_backup.md)
* [Performing Redshift Clusters Backup](aws_perform_redshift_backup.md)
* [Performing Redshift Serverless Backup](aws_perform_redshift_serverless_backup.md)
* [Performing EFS Backup](aws_perform_efs_backup.md)
* [Performing FSx Backup](aws_perform_fsx_backup.md)
* [Performing VPC Configuration Backup](aws_perform_vpc_backup.md)
* [Managing Backup Policies](aws_policies_ec2_manage.md)

Page updated 2026-05-21

