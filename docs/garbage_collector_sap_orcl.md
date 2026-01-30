---
title: "Configuring Retention Policy for Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/garbage_collector_sap_orcl.html"
last_updated: "12/17/2024"
product_version: "13.0.1.1071"
---

# Configuring Retention Policy for Backups


Veeam Plug-In for SAP on Oracle has a functionality that automatically deletes backup files which are older than specified number of days. For example, you can use it if a backup repository contains backup files that are no longer in the backup catalog.

1. To enable automatic deletion of backup files, run the following command.

|  |
| --- |
| SapOracleBackintConfigTool --set-force-delete |

1. Enter the number of days after which Veeam Plug-In will delete backup files on all configured backup repositories.

|  |
| --- |
| Garbage collector automatically deletes backup files older than the specified number of days.  Make sure the number of days value exceeds your retention policy.  To disable this functionality, set the number of days to 0.  Enter the number of days to delete backups after, between 7 and 999 [0]: |

By default, the force delete functionality is disabled (set to 0).

|  |
| --- |
| Important |
| A value for the number of days setting must be at least 1 backup generation period longer than the retention period for your Oracle Database backups. Otherwise, Veeam Plug-In will delete earliest backups created within the retention period. |


