---
title: "Database Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restoring_databases.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Database Recovery


With the configured Veeam Plug-In you can restore SAP HANA databases from the backups that reside in the Veeam backup repository.

To restore databases, you can use SAP HANA Cockpit, SAP HANA Studio or HDBSQL commands. Restore operations using SAP HANA tools are performed on the SAP HANA side. Keep in mind that examples provided in this section are for demonstrating purposes only. To see the full restore functionality of SAP HANA tools, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/6b94445c94ae495c83a19646e7c3fd56/c3c66b63bb571014b3e5ad8618cda1ad.html?version=2.0.06).

You can also use Veeam Explorer for SAP HANA to restore databases. Restore operations in Veeam Explorer for SAP HANA are performed on the Veeam Backup & Replication side.

|  |
| --- |
| Note |
| To restore data from a backup, the version of Veeam Plug-In must be the same or later than the version that created the backup. Restore with an earlier version of Veeam Plug-In from a backup created with a later version is not supported and may cause the restore to fail. This limitation applies to build numbers, not only major versions: for example, you cannot use Veeam Plug-In build 13.0.1.1071 to restore data from a backup created with build 13.0.1.2067. |

To learn how to recover SAP HANA databases from backups stored in Veeam backup repositories, see the following subsections:

* [Restoring Databases (HDBSQL Commands)](saphana_restore_scripts.md)
* [Restoring Databases (SAP HANA Studio)](saphana_restore_studio.md)
* [Restoring SYSTEMDB (SAP HANA Cockpit)](restore_sysdb_cockpit.md)
* [Restoring Tenant Databases with SAP HANA Cockpit](restore_tenantdb_cockpit.md)
* [Restore to Another Server (System Copy)](restore_saphana_other_server.md)
* [Restore from Backup Copy](restore_from_copy_saphana.md)
* [Restore from Hardened Repository](restore_from_immutable_saphana.md)
* [Restore with Veeam Explorer for SAP HANA](restore_vehana.md)

Page updated 2026-07-30

