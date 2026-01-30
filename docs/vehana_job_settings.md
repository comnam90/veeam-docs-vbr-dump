---
title: "Required Job Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_job_settings.html"
last_updated: "11/6/2025"
product_version: "13.0.1.1071"
---

# Required Job Settings


You can create backups of SAP HANA databases using application backup policies managed by Veeam Backup & Replication and backup jobs managed by a standalone Veeam Plug-In for SAP HANA.

* To create an application backup policy managed by Veeam Backup & Replication, do the following:

1. Add the source SAP HANA machine to a protection group. For more information, see [Creating Protection Group for Individual Computers](protection_group_individual.md).
2. Create an application backup policy using the protection group. For more information, see [Creating SAP HANA Backup Policy](create_policy_create_sap_hana.md).

* To create a backup job managed by a standalone Veeam Plug-In for SAP HANA, you can use HDBSQL scripts, or native SAP HANA tools such as SAP HANA studio and SAP HANA Cockpit. For more information, see [Database Protection](sap_hana_backup.md).

After the backups are successfully created using one of these methods, you can use Veeam Explorer for SAP HANA to restore your SAP HANA data.


