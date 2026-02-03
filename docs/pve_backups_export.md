---
title: "Exporting Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backups_export.html"
last_updated: "1/9/2026"
product_version: "13.0.1.1071"
---

# Exporting Backups


Exporting backups allows you to synthesize a complete and independent full backup file using restore points located in your backup repositories. That is, you can transform any backup chain into a standalone full backup file and save it to a repository or folder.

To export a backup, do the following:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, expand the job that created the backup, right-click the VM for which you want to synthesize a full backup file, and select Export backup.

Alternatively, expand the job that created the backup, select the VM and click Export Backup on the ribbon.

1. Complete the New Export wizard as described in section [Performing Export](performing_full_export.md).

Once the export operation completes, the exported backup will be displayed under the Backups > Disk (Exported) node in the Home view of the Veeam Backup & Replication console.

[![Exporting Backups](images/pve_backups_export.webp)](images/pve_backups_export.webp "Exporting Backups")


