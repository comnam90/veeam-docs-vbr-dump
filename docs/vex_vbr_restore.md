---
title: "Restore from Veeam Backup & Replication Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vex_vbr_restore.html"
last_updated: "10/8/2025"
product_version: "13.0.1.1071"
---

# Restore from Veeam Backup & Replication Backups


You can restore Microsoft Exchange data from backups created by Veeam Backup & Replication to the original location or other on-premises Microsoft organizations and Microsoft 365 organizations.

Consider the following:

* If your Veeam Explorer for Microsoft Exchange comes as part of Veeam Backup & Replication, the backup content is loaded automatically if you launch Veeam Explorer for Microsoft Exchange from a backup, as described in [Application Item Restore](restore_veeam_explorers.md). You can also add a Microsoft Exchange database manually, as described in [Adding Microsoft Exchange Databases](adding_exchange_databases.md).
* If your Veeam Explorer for Microsoft Exchange comes as part of a standalone Veeam Backup for Microsoft 365 installation, you cannot restore from Veeam Backup & Replication backups by default. To enable this functionality, install Veeam Backup & Replication on the machine and add a Microsoft Exchange database. For more information, see [Adding Microsoft Exchange Databases](adding_exchange_databases.md).

You can get the EDB or ADB files directly from the original Microsoft Exchange machine, or you can use Veeam Backup & Replication to restore guest OS files of the machine. For more information, see [Guest OS File Restore](guest_file_recovery.md).

Before restoring data, read the [Considerations and Limitations](vex_considerations.md) section.

In This Section

* [1-Click Restore](vex_vbr_restore_one_click.md)
* [Restore to On-Premises Microsoft Servers](vex_vbr_restore_onprem.md)
* [Restore to Microsoft 365 Organizations](vex_vbr_restore_ms365.md)


