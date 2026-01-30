---
title: "Data Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_hana_data_restore.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Data Restore


With the configured Veeam Plug-In for SAP HANA, you can restore SAP HANA databases from Veeam Plug-In backups that reside on Veeam backup repositories.

You can use the tools SAP HANA Studio, SAP HANA Cockpit, SAP HANA HDBSQL commands, or the Veeam Backup & Replication console to restore databases. Restore operations initiated with the SAP HANA tools are performed on the SAP HANA side. You can also use Veeam Explorer for SAP HANA to restore SAP HANA databases. Restore operations in Veeam Explorer for SAP HANA are performed on the Veeam Backup & Replication side.

Depending on the available type of Veeam Plug-In backups that will be the source for the restored databases, you can perform the following restore operations:

* Restoring from backup.

Restore SAP HANA databases from a Veeam Plug-In backup to the original server by using SAP HANA tools or the Veeam Backup & Replication console. For details, see [Database Recovery](restoring_databases.md).

You can also restore SAP HANA databases from a Veeam Plug-In backup to another server by using SAP HANA tools or the Veeam Backup & Replication console. For details, see [Restoring to Another Server (System Copy)](restore_saphana_other_server.md).

* Restoring from a backup copy.

Restore SAP HANA databases from backup copies created for Veeam Plug-In for SAP HANA backups. For details, see [Restore from Backup Copy](restore_from_copy_saphana.md).

Depending on the location of Veeam Plug-In backups that will be the source for the restored databases, you can also perform the following restore operations:

* Restoring from simple repositories.

Restore SAP HANA databases from Veeam Plug-In backups stored on supported types of repositories by using SAP HANA tools or Veeam Explorer for SAP HANA in the Veeam Backup & Replication console. For details, see [Veeam Backup Repositories](sap_repos.md).

* Restoring from hardened repositories.

Restore SAP HANA databases from hardened repositories by creating new backup job metadata files (.VACM) with data from available backup metadata files (.VASM). For details, see [Restore from Hardened Repository](restore_from_immutable_saphana.md).


