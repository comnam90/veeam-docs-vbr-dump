---
title: "Backup Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_chain.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Chain


If you enable image-level backups for an EC2 backup policy, the backup appliance creates a new backup in a backup repository during every backup session according to the backup policy schedule. A sequence of backups created during a set of backup sessions makes up a backup chain.

The backup chain includes backups of the following types:

* Full — a full backup stores a copy of the full EC2 image.
* Incremental — incremental backups store incremental changes of EC2 images.

To create a backup chain for an EC2 instance protected by a backup policy, the forever forward incremental backup method is implemented:

1. During the first backup session, the backup appliance copies the full EC2 image and creates a full backup in the backup repository. The full backup becomes a starting point in the backup chain.
2. During subsequent backup sessions, the backup appliance copies only those data blocks that have changed since the previous backup session, and stores these data blocks to incremental backups in the backup repository. The content of each incremental backup depends on the content of the full backup and the preceding incremental backups in the backup chain.

[![Backup Chain](images/aws_backup_chain.webp)](images/aws_backup_chain.webp "Backup Chain")

Full and incremental backups act as restore points for backed-up EC2 instances that let you roll back instance data to the necessary state. To recover an EC2 instance to a specific point in time, the chain of backups created for the instance must contain a full backup and a set of incremental backups dependent on the full backup.

If some backup in the backup chain is missing, you will not be able to roll back to the necessary state. For this reason, you must not delete individual files from the backup repository manually. Instead, you must specify retention policy settings that will let you maintain the necessary number of backups in the backup repository. For more information, see [EC2 Backup Retention](aws_retention_backup.md).

|  |
| --- |
| Note |
| If you change the backup repository in a schedule-based backup policy or in a storage template assigned to an SLA-based backup policy, the backup appliance will stop creating the backup chain in the previous repository and start creating a new one in the newly selected repository. |

Related Topics

* [Changed Block Tracking](aws_cbt.md)
* [Archive Backup Chain](aws_archive_chain.md)
* [EC2 Backup Retention](aws_retention_backup.md)

Page updated 2026-05-15

