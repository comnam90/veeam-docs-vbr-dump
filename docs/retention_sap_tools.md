---
title: "Deleting Backups Using SAP HANA Tools"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/retention_sap_tools.html"
last_updated: "9/9/2025"
product_version: "13.0.1.1071"
---

# Deleting Backups Using SAP HANA Tools


To configure retention policies for SAP HANA backups, you can use the SAP HANA housekeeping options:

* [Manual Deletion of Backups in SAP HANA Studio](#studio)
* [Configuring Retention Policy in SAP HANA Cockpit](#cockpit)
* [Deletion of Catalog and Backups Using Scripts](#script)

|  |
| --- |
| Important |
| If you delete backups from a backup catalog using scripts or SAP HANA Studio and don't select the option to delete backup physically from the backup location, backups will remain in the backup repository. In this case, we recommend to enable the options for physical deletion of backups in used SAP HANA retention tools or you must enable the [force deletion feature](garbage_collector_hana.md) of Veeam Plug-In for SAP HANA. Otherwise, you will run out of space on the backup repository. |

Manual Deletion of Backups in SAP HANA Studio

For details, see [this SAP article](https://help.sap.com/viewer/6b94445c94ae495c83a19646e7c3fd56/2.0.00/en-US/cac903c28b0e4301b39814ef41dbf568.html).

To physically delete the backups, you must select the Catalog and Backup Location option. Note that if you have physical backups in both the file system and a Veeam backup repository, you can choose to delete data backups in only one location.

Configuring Retention Policy in SAP HANA Cockpit

For details, see [this SAP article](https://help.sap.com/doc/85e9352c24fc4fcc816d41524a582b7a/2.9.0.0/en-US/SAP_HANA_Administration_with_SAP_HANA_Cockpit_en.pdf). Note that the retention policy functionality is supported only in SAP HANA 2.0 SPS 03 and later versions.

When you configure a retention policy in SAP HANA Cockpit, make sure that you have selected the Also delete physically from Backint check box in the Options for Backup Deletion section. Otherwise the backups will not be deleted from the repository.

Deletion of Catalog and Backups Using Scripts

Deletion of catalog and backups using scripts. For details see [this SAP article](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/2.0.03/en-US/22275913eb9e4a5bb539fc8df3da77f1.html).

To physically delete backups from the backup repository, you must include the WITH BACKINT and WITH FILE options in the script.


