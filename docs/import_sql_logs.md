---
title: "Importing Transaction Logs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_sql_logs.html"
last_updated: "2/10/2025"
product_version: "13.0.1.1071"
---

# Importing Transaction Logs


You cannot import transaction log backups without VM backups (as there will be no restore point to which the transaction logs can be applied).

To import a VM backup with transaction log backups, do either of the following:

* Import a backup metadata file (VBM). In this case, Veeam Backup & Replication will automatically import the database backup and log backups.
* Import a full backup file (VBK). In this case, Veeam Backup & Replication will browse the required log backups and import them.


