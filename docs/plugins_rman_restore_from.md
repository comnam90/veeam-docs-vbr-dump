---
title: "Restoring from Oracle RMAN Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_rman_restore_from.html"
last_updated: "5/28/2026"
product_version: "13.0.2.29"
---

# Restoring from Oracle RMAN Backup


The Oracle RMAN backup restore option in Veeam Backup & Replication allows you to recover Oracle databases from backups. You can restore databases to the original Oracle server or to a new Oracle server as needed. To restore Oracle databases Veeam Backup & Replication uses Veeam Explorer for Oracle.

To restore a database from an RMAN backup in Veeam Backup & Replication:

1. Open the Home view.
2. In the inventory pane, click Backups.
3. In the working area, right-click the backup and select Restore from Oracle RMAN backup.

Clicking the Restore from Oracle RMAN backup option starts Veeam Explorer for Oracle, which allows you to restore the required database. For detailed instructions on restoring databases with Veeam Explorer for Oracle, see [Restoring from RMAN Plug-in Backups](rman_backups.md).

For more information on restore procedures, see [Database Recovery](oracle_db_restore.md).

[![Disable Backup Job](images/plugins_rman_restore_from.webp)](images/plugins_rman_restore_from.webp "Disable Backup Job")


