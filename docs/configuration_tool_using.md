---
title: "Using Veeam Backup Configuration Tool"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/configuration_tool_using.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Using Veeam Backup Configuration Tool

In this article

The Veeam Backup Configuration tool is located on the backup server in the installation folder of Veeam Backup & Replication. The default path is %ProgramFiles%\Veeam\Backup and Replication\Backup\Veeam.Backup.Configuration.Tool.exe. If the default path was changed, you can find the actual path in the following registry value: [HKEY\_LOCAL\_MACHINE\SOFTWARE\Veeam\Veeam Backup and Replication] CorePath.

To run the tool, open the command prompt on the backup server and change the current folder to the folder where Veeam Backup Configuration tool is located.

|  |
| --- |
| Important |
| To run the Veeam Backup Configuration tool, you must use an account with administrative rights on the local machine. |

Syntax

The Veeam Backup Configuration tool provides parameter sets that allow you to:

* Display help information for the Veeam Backup Configuration tool.

|  |
| --- |
| Veeam.Backup.Configuration.Tool /? |

* Analyze a configuration backup file.

|  |
| --- |
| Veeam.Backup.Configuration.Tool /file:value /analyzefile |

* Check whether a configuration backup is not corrupted.

|  |
| --- |
| Veeam.Backup.Configuration.Tool /file:value /checkfile |

* Analyze a configuration database.

|  |
| --- |
| Veeam.Backup.Configuration.Tool /analyzedatabase [/servername:value] [/instancename:value] [/serverport:value] [/initialcatalog:value] [/login:value][/password:value] |

* Back up a configuration database.

|  |
| --- |
| Veeam.Backup.Configuration.Tool /file:value /backupdatabase [/servername:value][/instancename:value] [/serverport:value] [/initialcatalog:value] [/login:value] [/password:value] [/cryptfile] |

Parameters

| Parameter | Description |
| --- | --- |
| /file:value | Specifies a path to the configuration backup file. |
| /analyzefile | Analyzes a configuration backup file. |
| /checkfile | Checks whether the configuration backup is not corrupted. |
| /analyzedatabase | Analyzes a configuration database. |
| /backupdatabase | Backs up a configuration database. |
| /databaseengine | Specifies a database engine |
| /servername:value | Specifies a name of a SQL server. |
| /instancename:value | Specifies a name of a SQL instance. |
| /serverport:value | Specifies a port number of a SQL server. The tool will use this port to access the SQL server. |
| /initialcatalog:value | Specifies a name of a SQL database. |
| /login:value | Specifies a username that the tool will use to authenticate against a SQL server. |
| /password:value | Specifies a password that the tool will use to authenticate against a SQL server. |
| /cryptfile | Defines that the tool will encrypt a configuration backup file. |
| /verbose | Enables verbose output mode. |

Examples

Example 1

This example shows how to analyze the 193022052014.bco configuration backup file. After you start the command, the command prompt will return the output.

|  |
| --- |
| Veeam.Backup.Configuration.Tool.exe /file:"c:\my files\193022052014.bco"  /analyzefile /verbose |

Example 2

This example shows how to analyze the 193022052014.bco configuration backup file and back up the configuration database. The command will contain the following settings of the configuration database:

* The configuration database is located at the WIN2008R2 SQL server.
* The name of the SQL instance is VeeamSql2008.
* The name of the SQL database is VeeamBackup.

|  |
| --- |
| Veeam.Backup.Configuration.Tool.exe /file:c:\backups\091323052014.bco  /backupdatabase /servername:WIN2008R2 /instancename:VeeamSql2008  /initialcatalog:VeeamBackup |

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
