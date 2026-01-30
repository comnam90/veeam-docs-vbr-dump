---
title: "Force Deleting Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_mssql_retention_force.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Force Deleting Backups


Veeam Plug-In has a functionality that automatically force deletes backup files which are older than specified number of days. For example, it may be helpful if a database was renamed and backups for this database created before the renaming are no longer processed by Veeam Plug-In.

To delete backup files, do the following:

1. On Microsoft SQL Server, navigate to the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\ folder.
2. Run the following command:

|  |
| --- |
| MSSQLConfigTool --set-force-delete --days <days> --bkp <backup\_name> --repo <repository\_name> --force |

where:

* <days> is the retention period in days. After this period, Veeam Plug-In automatically force deletes the specified backup files.
* <backup\_name> is the name of the backup. By default, Veeam Plug-In names backup files after the protected Microsoft SQL Server.
* <repository\_name> is the name of the repository where backup files are located.

Also, you can specify the --force option. This option allows to override additional input prompts and error messages.

For example:

|  |
| --- |
| MSSQLConfigTool --set-force-delete --days 100 --bkp SRV001 --repo "Default Backup Repository" |

Considerations and Limitations

Before you delete backup files, consider the following:

* Make sure the number of days specified in the command exceeds the retention policy configured in the Back Up Database wizard. For details, see [Specify Backup Options](backup_job_options.md).
* Make sure the number of days specified in the command exceeds the immutability period configured for the backup repository.
* If backups that you want to delete are stored in the scale-out repository:

* Make sure these backups are not on the extent that is in maintenance mode. For details, see [Maintenance Mode](sobr_maintenance.md).
* Make sure backups are not stored in the Archive tier.

* The command cannot delete imported backups.


