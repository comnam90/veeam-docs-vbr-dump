---
title: "Managing Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_repositories.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Repositories


Veeam Plug-in for AWS uses Amazon S3 buckets as target locations for EC2 and RDS image-level backups, additional copies of Amazon VPC backups, indexes of EFS file systems and configuration backups of backup appliances. To store backups in Amazon S3 buckets, configure repositories. Veeam Plug-in for AWS version 13.11. comes with 2 types of repositories:

* Backup repository — a folder created by backup appliances in an Amazon S3 bucket managed by AWS users in AWS.
* Storage vault — a folder created by Veeam Data Cloud in an Amazon S3 bucket managed by Veeam in Veeam Data Cloud Vault.

|  |
| --- |
| Important |
| A backup must not be managed by multiple backup appliances simultaneously. Retention sessions running on different backup appliances may corrupt backups stored in the repository, which may result in unpredictable data loss. |

In This Section

* [Adding Storage Vaults Using Console](aws_repositories_add_vault_console.md)
* [Adding Backup Repositories Using Console](aws_repositories_add_console.md)
* [Adding Backup Repositories Using Web UI](aws_repositories_add_ui.md)
* [Editing Backup Repository Settings](aws_repositories_edit.md)
* [Rescanning Backup Repositories](aws_rescan_repositories.md)
* [Removing Backup Repositories](aws_repositories_remove.md)

Page updated 2026-07-13

