---
title: "Configuring Force Deletion of Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/garbage_collector_hana.html"
last_updated: "9/9/2025"
product_version: "13.0.1.1071"
---

# Configuring Force Deletion of Backups


In the main scenario, when using Veeam Plug-In for SAP HANA, you must configure the retention policy using native SAP HANA tools. For details, see [Retention of SAP HANA Backups](saphana_retention.md).

Veeam Plug-In for SAP HANA has a functionality that automatically force deletes backup files which are older than specified number of days. For example, you can use it if a backup repository contains backup files that are no longer in the backup catalog.

If you use SAP HANA 2.0 SPS 07 or later and you set Veeam Plug-In for SAP HANA to force delete backup files, consider that Veeam Plug-In will also delete backups that are flagged by as retained using SAP HANA functionality.

To enable force deletion of backup files, do the following:

1. On the SAP HANA server, run the following command.

|  |
| --- |
| SapBackintConfigTool --set-force-delete |

1. Enter the number of days after which Veeam Plug-In will force delete backup files on all configured Veeam backup repositories.

|  |
| --- |
| Garbage collector automatically deletes backup files older than the specified number of days.  Make sure the number of days value exceeds your retention policy.  To disable this functionality, set the number of days to 0.  Enter the number of days to delete backups after, between 7 and 999 [0]: |

By default, the force delete functionality is disabled (set to 0).

|  |
| --- |
| Important |
| * A value for the number of days setting must be at least 1 backup generation period longer than the retention period for your SAP HANA backups. Otherwise, Veeam Plug-In will delete earliest backups created within the retention period. * If a backup repository contains backups older than the specified retention period, Veeam Plug-In removes old backup files only after the next run of the Backint backup. * If you use SAP HANA 2.0 SPS 07 or later, Veeam Plug-In will be able to force delete backups that are flagged as retained. To learn more about the flag, see [this SAP article](https://help.sap.com/docs/SAP_HANA_PLATFORM/42668af650f84f9384a3337bcd373692/75aedc1d3d634dcc90dbeb7b908cb58e.html). |


