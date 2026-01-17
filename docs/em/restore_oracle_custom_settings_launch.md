---
title: "Step 1. Launch Oracle Restore Wizard"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/restore_oracle_custom_settings_launch.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---


In this article

To launch the Oracle Restore wizard, do the following:

1. Open the Items tab and click Oracle Database.
2. In the Server field, enter a name of the Oracle server hosting the database you need to restore.

Alternatively, click the Pick from List link to select a machine from the list of available Oracle backups.

1. From the Database to restore list, select Oracle home and the database you need. Consider that user credentials for carrying out the restore procedure will be picked as follows:

1. Veeam Backup Enterprise Manager will try to use the account of the backup job that contains the Oracle server machine, or the account which is currently logged in.
2. If this account does not have sufficient rights to perform the restore procedure (for example, in case of imported backup), you will be prompted to supply the necessary credentials. Make sure the account has access to the original machine guest OS (Windows or Linux); if restoring an Oracle 12 Database on Windows server, then you may need to enter password for Oracle home.

1. To specify a restore point from which to restore the database, in the Restore point field, click the calendar icon and select the necessary date when backup was performed and a restore point created on that date. By default, the latest valid restore point is selected.
2. For a database backed up with transaction log backup turned on, you can also select the necessary point in time using the Point in time slider. The slider displays the following timestamps (relative to the currently selected restore point):

* The beginning point refers to the previous restore point of the Oracle machine that contains the selected database backup. If the previous restore point (server backup) is not found, or the database backup does not exist in it, then the beginning point refers to the current restore point.

* The ending point refers to the next restore point that contains the selected database backup. If the next restore point (server backup) and the associated transaction log backup are not found, or if the database backup does not exist in the server backup, then the ending point will refer to the current restore point. If the next restore point (server backup) is not found, but the transaction log backup exists for the preceding period, then the ending point refers to the latest log backup time.

For more information on configuring transaction log backup, see [Oracle Archived Redo Log Settings](jobs_aap_oracle.md).

1. In the Restore to section, select the Alternative location option.
2. Click Restore.

[![Launching Oracle Restore Wizard](images/em_item_restore_oracle.webp)](images/em_item_restore_oracle.webp "Launching Oracle Restore Wizard")

Page updated 11/10/2025

Page content applies to build 13.0.1.1071
