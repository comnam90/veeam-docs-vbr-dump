---
title: "Restore from Veeam Backup & Replication Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_from_vbr_backups.html"
last_updated: "10/6/2025"
product_version: "13.0.1.1071"
---

# Restore from Veeam Backup & Replication Backups


You can restore Microsoft SharePoint data from backups created by Veeam Backup & Replication to the original or another location.

Consider the following:

* If your Veeam Explorer for Microsoft SharePoint comes as part of Veeam Backup & Replication, the backup content is loaded automatically if you launch Veeam Explorer for Microsoft SharePoint from a backup, as described in [Application Item Restore](restore_veeam_explorers.md). You can also add a Microsoft SharePoint database manually, as described in [Adding Microsoft SharePoint Databases](vesp_adding_sp_databases.md).
* If your Veeam Explorer for Microsoft SharePoint comes as part of a standalone Veeam Backup for Microsoft 365 installation, you cannot restore from Veeam Backup & Replication backups by default. To enable this functionality, install Veeam Backup & Replication on the machine and add a Microsoft SQL Server database that contains your Microsoft SharePoint data. For more information, see [Adding Microsoft SharePoint Databases](vesp_adding_sp_databases.md).

To get the database files, use any of the following methods:

* Get the database files directly from the original Microsoft SharePoint machine.
* Use Veeam Explorer for Microsoft SQL Server to export database files from restore points created by Veeam Backup & Replication. For more information, see [Exporting as MDF](vesql_exporting_mdf.md).
* Use Veeam Backup & Replication to restore guest OS files of the machine. For more information, see [Guest OS File Restore](guest_file_recovery.md).

Before restoring data, read the [Considerations and Limitations](vesp_recovery_specials.md) section.

In This Section

* [Restoring Sites](vesp_vbr_restore_sites.md)
* [Restoring Document Libraries and Lists](vesp_vbr_restore_document_libraries.md)
* [Restoring Documents and List Items](vesp_vbr_restore_items.md)


