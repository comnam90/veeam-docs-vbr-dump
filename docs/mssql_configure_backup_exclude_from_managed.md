---
title: "Backing Up SQL Databases with Standalone Backup Job"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mssql_configure_backup_exclude_from_managed.html"
last_updated: "12/1/2025"
product_version: "13.0.1.1071"
---

# Backing Up SQL Databases with Standalone Backup Job


If you have Veeam Plug-In for Microsoft SQL Server managed by Veeam Backup & Replication, you have a possibility to exclude databases from the backup scope of an application backup policy configured in the Veeam Backup & Replication console. As a result you can back up such databases using a separate standalone backup job triggered from Microsoft SQL Server. In this case, Veeam Backup & Replication processes the whole SQL server in the managed mode, but certain databases are processed by Veeam Plug-In in the standalone mode. This may be useful if you want to back up database manually from Microsoft SQL Server and avoid creating 2 backup chains for the same database.

Keep in mind that this functionality is available only for Veeam Plug-In for Microsoft SQL Server.

To exclude databases from the backup scope of an application backup policy, perform the following steps on the Microsoft SQL Server side:

1. On the Veeam Backup & Replication side, make sure that the database is not in the backup scope of existing application backup policies. For details on how to see the backup scope of a policy, see [Specify Databases](policy_microsoft_sql_server_databases.md).
2. On the Microsoft SQL Server side, navigate to the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\ folder.
3. Configure a separate repository for standalone backup jobs started from the Microsoft SQL Server side. To do that, run the MSSQLConfigTool.exe command with the --set-repository parameter:

|  |
| --- |
| MSSQLConfigTool.exe --set-repository |

1. Exclude databases you want to process with Veeam Plug-In in the standalone mode:

|  |
| --- |
| MSSQLConfigTool.exe --exclude-from-managed-mode --instance "<instance\_name>" --d "<database\_name>" |

where:

* <instance\_name> is a name of the instance whose databases you want to exclude from the backup scope of an application backup policy.
* <database\_name> is a name of the database you want to exclude from the backup scope of an application backup policy. If you want to specify several databases, specify each database with a separate --d parameter.

For example:

|  |
| --- |
| MSSQLConfigTool.exe --exclude-from-managed-mode --instance "MSSQLSERVER" --d "db1" --d "db2" |

After that, you can back up specified databases in the same way as you back up databases protected by Veeam Plug-In operating in the standalone mode. For details, see [Performing Backup](mssql_protection.md). Other databases of this SQL instance are still processed by an application backup policy in the usual manner.

In the Veeam Backup & Replication console, after the first successful backup session by Veeam Plug-In operating in the standalone mode, a separate backup job appears in the Jobs node and a separate backup file appears in the Backups node.

Alternatively, you can configure a list of exclusions in the veeam\_config.xml file:

|  |
| --- |
| <PluginParameters> |

Removing Database from List of Exclusions

If you want to return the database to the management scenario and back up the database from the Veeam Backup & Replication side:

1. On Microsoft SQL Server, navigate to the %PROGRAMFILES%\Veeam\Plugins\Microsoft SQL\ folder.
2. To remove the database from the list of exclusions, run the MSSQLConfigTool.exe command with the --exclude-from-managed-mode parameter:

|  |
| --- |
| MSSQLConfigTool.exe --exclude-from-managed-mode --remove-from-exclusions --instance "<instance\_name>" --d "<database\_name>" |

where:

* <instance\_name> is a name of the instance whose databases you want to exclude from the backup scope of an application backup policy.
* <database\_name> is a name of the database you want to exclude from the backup scope of an application backup policy. If you want to specify several databases, specify each database with a separate --d parameter.

For example:

|  |
| --- |
| MSSQLConfigTool.exe --exclude-from-managed-mode --remove-from-exclusions --instance "MSSQLSERVER" --d "db1" --d "db2" |

After that, you can back up removed databases as usual in the management scenario. For details, see [Getting Started](quickstart.md).


