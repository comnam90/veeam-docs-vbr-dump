---
title: "RPO Warning Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_backup_copy_advanced_rpo_monitor.html"
last_updated: "8/25/2025"
product_version: "13.0.1.1071"
---

# RPO Warning Settings


You can instruct a backup copy job to display a warning if a newly created restore point or transaction log is not copied within the desired recovery point objective (RPO). The RPO is counted down from the moment when the source backup job finishes and is ready to be copied.

To mark a job with the Warning status when the RPO is exceeded, do the following:

1. At the Target step of the wizard, click Advanced job settings.
2. Click the RPO Monitor tab.
3. Select the When new backup is not copied within check box.
4. In the fields on the right, specify the desired RPO in minutes, hours or days. If you specify days, RPO monitor will consider calendar days instead of the 24 hours period.
5. If you have enabled copying of log backups, select the When new log backup is not copied within check box.
6. In the fields on the right, specify the desired RPO in minutes, hours or days.

![RPO Warning Settings](images/backup_copy_advanced_rpo_mongo.webp)


