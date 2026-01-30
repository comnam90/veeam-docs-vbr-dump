---
title: "Importing Backup Files from Scale-Out Backup Repositories"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_sobr.html"
last_updated: "2/9/2024"
product_version: "13.0.1.1071"
---

# Importing Backup Files from Scale-Out Backup Repositories


You cannot import a backup directly from the scale-out backup repository. When you perform backup import, you cannot browse the whole scale-out backup repository. Veeam Backup & Replication lets you browse only through individual extents.

To import a backup from the scale-out backup repository, you must place backup files from all extents to one staging folder. The staging folder can reside on any server added to the backup infrastructure. After that, you can import the backup as usual.

|  |
| --- |
| Tip |
| If you need to import all backups stored in a scale-out backup repository, rescan the repository. In this case, you do not need to place files in one folder; Veeam Backup & Replication will import backups automatically. For more information, see [Rescanning Backup Repositories](rescanning_backup_repositories.md). |


