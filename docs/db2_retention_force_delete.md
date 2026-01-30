---
title: "Configuring Force Deletion of Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_retention_force_delete.html"
last_updated: "12/17/2024"
product_version: "13.0.1.1071"
---

# Configuring Force Deletion of Backups


Veeam Plug-In for IBM Db2 has a functionality that automatically force deletes backup files which are older than specified number of days. For example, you can use it if a backup repository contains backup files that are no longer in the backup catalog.

To enable force deletion of backup files, do the following:

1. On the machine with Veeam Plug-In, run the following command.

|  |
| --- |
| DB2ConfigTool --set-force-delete |

1. Enter the number of days after which Veeam Plug-In will force delete backup files on all configured Veeam backup repositories.

|  |
| --- |
| Garbage collector automatically deletes backup files older than the specified number of days.  Make sure the number of days value exceeds your retention policy.  To disable this functionality, set the number of days to 0.  Enter the number of days to delete backups after, between 7 and 999 [0]: |

By default, the force delete functionality is disabled (set to 0).

|  |
| --- |
| Important |
| If a backup repository contains backups older than the specified retention period, Veeam Plug-In removes old backup files only after the next backup run. |


