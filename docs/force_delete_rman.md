---
title: "Configuring Force Deletion of Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/force_delete_rman.html"
last_updated: "3/28/2025"
product_version: "13.0.1.1071"
---

# Configuring Force Deletion of Backups


In the main scenario, when using Veeam Plug-In for Oracle RMAN, you must configure the retention policy using native Oracle RMAN tools. For details, see [Configuring Retention Policy](retention_rman_config.md).

Veeam Plug-In for Oracle RMAN has a functionality that automatically force deletes backup files which are older than specified number of days. For example, you can use it if a backup repository contains backup files that are no longer in the backup catalog.

To enable force deletion of backup files, do the following:

1. On the Oracle server, run the following command.

* For Linux and Unix:

|  |
| --- |
| OracleRMANConfigTool --set-force-delete |

* For Microsoft Windows:

|  |
| --- |
| OracleRMANConfigTool.exe --set-force-delete |

By default, the OracleRMANConfigTool.exe file is located in %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN.

1. Enter the number of days after which Veeam Plug-In will force delete backup files on all configured Veeam backup repositories.

|  |
| --- |
| Garbage collector automatically deletes backup files older than the specified number of days.  Make sure the number of days value exceeds your retention policy.  To disable this functionality, set the number of days to 0.  Enter the number of days to delete backups after, between 7 and 999 [0]: |

By default, the force delete functionality is disabled (set to 0).

|  |
| --- |
| Important |
| * A value for the number of days setting must be at least 1 backup generation period longer than the retention period for your Oracle Database backups. Otherwise, Veeam Plug-In will delete earliest backups created within the retention period. * If a backup repository contains backups older than the specified retention period, Veeam Plug-In removes old backup files only after the next run of the RMAN backup. |


