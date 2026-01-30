---
title: "Backup Copy for IBM Db2 Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_backup_copy.html"
last_updated: "3/7/2025"
product_version: "13.0.1.1071"
---

# Backup Copy for IBM Db2 Backups


One backup does not provide the necessary level of safety. The primary backup may get destroyed together with production data, and you will have no backups from which you can restore data.

To build a successful data protection and disaster recovery plan, it is recommended that you follow the 3-2-1 rule:

* 3: You must have at least three copies of your data: the original production data and two backups.
* 2: You must use at least two different types of media to store the copies of your data, for example, local disk and cloud.
* 1: You must keep at least one backup offsite, for example, in the cloud or in a remote site.

Thus, you must have at least two backups and they must be in different locations. If a disaster takes out your production data and local backup, you can still recover from your offsite backup.

In This Section

* [Creating Backup Copy Job](db2_backup_copy_create.md)
* [Converting Backup Copy to Backup](db2_backup_copy_map.md)


