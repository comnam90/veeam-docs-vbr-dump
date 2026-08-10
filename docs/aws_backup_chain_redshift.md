---
title: "Backup Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_chain_redshift.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Chain


During every backup session, the backup appliance creates a new cloud-native backup for each Redshift cluster added to the backup policy. To create the backup, the appliance uses the [AWS Backup service](https://docs.aws.amazon.com/redshift/latest/mgmt/managing-aws-backup.html). A sequence of cloud-native backups created during a set of backup sessions makes up a backup chain.

[![Redshift Backup Chain](images/aws_redshift_backup_chain.webp)](images/aws_redshift_backup_chain.webp "Redshift Backup Chain")

Each Redshift backup in the backup chain contains encrypted metadata. Metadata stores information about the protected cluster, the backup policy that created the backup, and the date, time and applied retention settings. The backup appliance uses metadata to identify outdated backups, to load the configuration of source cluster during recovery operations, and so on.

|  |
| --- |
| Notes |
| * Due to [AWS Backup service limitations](https://docs.aws.amazon.com/aws-backup/latest/devguide/backup-feature-availability.html#features-by-resource), during every backup session, the backup appliance creates a full backup in the regular backup chain. * Redshift backups created manually are not included into the Redshift backup chain. Therefore, these backups are not removed automatically according to retention policy settings. To learn how to remove them, see [Removing Redshift Clusters Backups Created Manually](aws_backups_remove_individual_redshift.md). |

Redshift backups act as independent restore points for backed-up clusters. If you remove any backup, it will not break the Redshift backup chain — you will still be able to roll back cluster data to any existing restore point. The period of time during which Redshift backups are kept in the Redshift backup chain is defined by retention policy settings. For more information, see [Redshift Backup Retention](aws_retention_backup_redshift.md).

Page updated 2026-05-15

