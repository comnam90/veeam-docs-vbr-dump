---
title: "Configuring Veeam Plug-In for AWS"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_configuration.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Veeam Plug-In for AWS


To start working with Veeam Plug-in for AWS, perform a number of steps for its configuration:

1. [Add backup appliances to the backup infrastructure](aws_connect_appliance.md).
2. [Add repositories that will be used to store backed-up data](aws_repositories.md).

This step applies if you plan to protect EC2 or DB instances with image-level backups, to perform EFS indexing operations, to back up backup appliance configuration and to keep additional copies of Amazon VPC configuration backups in Amazon S3.

1. Configure the added backup appliances:

1. [Add IAM roles to access AWS services and resources that belong to a standalone AWS account](aws_accounts_iam_roles.md).
2. [[Optional] Add AWS Organizations to access resources that belong to AWS accounts across organizational units within the organizations](aws_managing_organizations.md).
3. [[Optional] Add users to control access to backup appliances](aws_accounts_vba_users.md).
4. [[Optional] Add database accounts to access databases of PostgreSQL DB instances](aws_accounts_database.md).
5. [[Optional] Configure worker instance settings](aws_workers.md).

If you do not configure settings for worker instances, backup appliances will use the default settings of AWS Regions where worker instances will be deployed.

1. [[Optional] Configure policy templates that will be used by SLA-based backup policies](aws_sla_storage_manage.md).
2. [[Optional] Configure private network deployment, global retention, email notification and single-sign-on settings](aws_general_settings.md).

|  |
| --- |
| Note |
| Even after you add IAM roles or AWS Organizations that manage your AWS resources and configure all the necessary settings, Veeam Plug-in for AWS will not populate [the list of resources on the Resources page](aws_aws_resources.md) — unless you create backup policies and specify regions where the AWS resources belong, as described in section [Performing Backup](aws_backup.md). |

Page updated 2026-07-09

