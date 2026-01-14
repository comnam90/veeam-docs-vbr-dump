---
title: "Step 8. Review Restore Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_vbr_review.html"
last_updated: "5/21/2025"
product_version: "13.0.1.1071"
---

# Step 8. Review Restore Settings

In this article

At the Restore step of the wizard, Veeam Backup & Replication will display the progress on the restore process. Wait for the restore process to complete and click Next.

![Step 8. Review Restore Settings](images/vbr_restore_review.webp)

If you have chosen to restore data in the Migrate mode and the configuration backup file does not meet the Migrate mode requirements, Veeam Backup & Replication will display a warning and offer you to switch to the Restore mode. The Restore mode requires more time but guarantees that information about all new restore points will be available in the restored database.

* To switch to the Restore mode, in the warning window click Yes.
* To carry on data restore in the Migrate mode, in the warning window click No.
* To stop the restore process, in the warning window click Cancel.

For more information, see [Migrating Veeam Backup & Replication to Another Backup Server](vbr_config_migrate.md).

Page updated 5/21/2025

Page content applies to build 13.0.1.1071
