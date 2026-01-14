---
title: "Step 4. Specify Recovery Type"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_restore_single_pit_specify_recovery_type.html"
last_updated: "8/18/2025"
product_version: "13.0.1.1071"
---

# Step 4. Specify Recovery Type

In this article

At this step of the wizard, specify whether to restore your database to a specific data backup or a point in time.

* Select Recover to a specific data backup to restore the database to a specific data backup. You can select the necessary backup at the next step of the wizard.

Note that this action clears all transaction logs stored in the system memory that were not yet saved to the log backups at the time of backup.

* Select Recover to specific point in time to restore the database to a specific point in time.

1. In the Date field, specify the date and time of the state to which you want to restore your database.
2. From the Time zone drop-down list, select the time zone for the time specified in the Date field. By default, Veeam Explorer for SAP HANA displays the time zone of the backup server.
3. Select the Initialize log area check box to remove all log segments in the log area or, in other words, to clear the part of the system memory that temporarily stores transaction logs before they are moved to the log backups. This allows you to restore the database to the latest available log backup before the selected point in time.

Note that initializing the log area may cause loss of in-memory data, so perform this action only if the log area is unavailable. If you do not initialize the log area when the log area is unavailable, the restore operation will fail. To resolve this issue, repeat the restore operation with the Initialize log area check box selected.

If you select the Recover to a specific data backup option, proceed to the next step of the wizard. If you select the Recover to a specific point in time option, click Restore.

[![Specifying Recovery Type](images/vehana_specify_single_recovery_pit.webp)](images/vehana_specify_single_recovery_pit.webp "Specifying Recovery Type")

Page updated 8/18/2025

Page content applies to build 13.0.1.1071
