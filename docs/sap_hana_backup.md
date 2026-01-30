---
title: "Database Protection"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_hana_backup.html"
last_updated: "10/18/2024"
product_version: "13.0.1.1071"
---

# Database Protection


After you configure Veeam Plug-In, you can back up databases with SAP HANA backup tools. Veeam Plug-In will automatically transfer data to the Veeam backup repository and store this data in Veeam proprietary format. The backup process itself is performed by SAP HANA Backint.

Keep in mind that examples in this section are provided only for demonstrating purposes. For details on full backup functionality of SAP HANA tools, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/c3a57273bb571014a747a289a3198e15.html?locale=en-US&version=2.0.06).

|  |
| --- |
| Important |
| Veeam Plug-In transfers backup data to the Veeam backup repository only when you perform the backup using SAP Backint. |

|  |
| --- |
| Note |
| Backups created by Veeam Plug-Ins cannot be used as a source for file to tape or backup to tape jobs. |

To back up SAP HANA databases, you can use SQL commands or SAP HANA administration tools. For details, see the following subsections:

* [Database Backup (HDBSQL Scripts)](backup_saphana_scripts.md)
* [Database Backup (SAP HANA Studio)](backup_saphana_studio.md)
* [Database Backup (SAP HANA Cockpit)](backup_hana_cockpit.md)

* [Backup Job in Veeam Backup & Replication](backup_console_vbr.md)


