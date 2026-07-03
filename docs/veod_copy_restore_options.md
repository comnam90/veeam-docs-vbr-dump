---
title: "Step 6. Specify Restore Options"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veod_copy_restore_options.html"
last_updated: "3/19/2026"
product_version: "13.0.2.29"
---

# Step 6. Specify Restore Options


At this step of the wizard, select check boxes next to the restore options that you want to apply and click Restore.

You can select the following options:

* Changed items. Allows you to restore data that has been modified in your production environment.
* Missing items. Allows you to restore missing items.

* Restore only latest version. Allows you to restore only the latest version of items. If this check box is selected, you can select one of the following options:

* Merge. To merge an existing and a backup version of items.
* Overwrite. To overwrite data in the production environment.

If the Restore only latest version check box is not selected, backed-up versions of items will be merged with the existing versions in the production environment.

* Restore shared access. Allows you to restore shared access.

* Send a notification by email to the users with permissions to the file. Select this check box if you want to notify users about items restore. Veeam Explorer for Microsoft OneDrive will notify users with whom items have been shared. You can select this check box only if the Restore shared access check box is selected.

|  |
| --- |
| Note |
| The Send a notification by email to the users with permissions to the file check box is only available when restoring data from backups created by Veeam Backup for Microsoft 365 for Microsoft 365 organizations. |

![Step 6. Specify Restore Options](images/restoring_onedrive_5.webp "Specify Restore Options")


