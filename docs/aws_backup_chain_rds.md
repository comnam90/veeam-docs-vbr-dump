---
title: "Backup Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_chain_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Chain


The forever forward incremental backup method is not implemented for DB instances — during every backup session the backup appliance creates a full backup in the regular backup chain.

Each RDS backup in the backup chain contains encrypted metadata that stores information about the protected DB instance, the backup policy that created the backup, as well as the date, time and configured retention settings. The backup appliance uses metadata to identify outdated backups, to retrieve information on the source instance configuration during recovery operations, and so on.

RDS backups act as independent restore points for backed-up DB instances. If you remove any backup, it will not break the backup chain — you will still be able to roll back data to any existing restore point.

The period of time during which RDS backups are kept in the backup chain is defined by retention policy settings. For more information, see [RDS Backup Retention](aws_retention_backup_rds.md).

Related Topics

* [Archive Backup Chain](aws_archive_chain_rds.md)
* [RDS Backup Retention](aws_retention_backup_rds.md)

Page updated 2026-05-15

