---
title: "Force Deleting Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_mssql_retention_force.html"
last_updated: "3/26/2026"
product_version: "13.0.1.2067"
---

# Force Deleting Backups


Using Veeam Plug-In for Microsoft SQL Server, you can manually deletes backups of specific databases which are older than the specified age limit. To learn more about the logic behind the force delete operation, see [Force Delete Operation](mssql_retention_tools_force_delete.md).

Considerations and Limitations

Before you delete database backups, consider the following:

* Use the force delete operation with caution, as it may lead to data loss. For example, the force delete operation can remove backups earlier than it is intended according to the retention policy.
* Make sure the number of days specified in the command exceeds the immutability period configured for the backup repository. Otherwise, the command will not be able to delete immutable backups.
* If backups that you want to delete are stored in the scale-out repository:

* Make sure these backups are not on the extent that is in maintenance mode. For details, see [Maintenance Mode](sobr_maintenance.md).
* Make sure backups are not stored in the Archive tier.

* The command cannot delete imported backups.

Force Delete

To delete database backup from the backup file, do the following:

1. On Microsoft SQL Server, navigate to the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\ folder.
2. Run the following command:

|  |
| --- |
| MSSQLConfigTool --set-force-delete --days <days> --bkp <backup\_name> --repo <repository\_name> --force |

where:

* <days> is the age limit in days. Veeam Plug-In force deletes all database backups if all of them are older than the specified number of days.
* <backup\_name> is the name of the backup. By default, Veeam Plug-In names backup files after the protected Microsoft SQL Server.
* <repository\_name> is the name of the repository where backup files are located.

Also, you can specify the --force option. This option allows to override additional input prompts and error messages.

For example:

|  |
| --- |
| MSSQLConfigTool --set-force-delete --days 100 --bkp SRV001 --repo "Default Backup Repository" |


