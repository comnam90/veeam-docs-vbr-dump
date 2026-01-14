---
title: "em_installation_byb"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_installation_byb.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---


In this article

Before you install Veeam Backup Enterprise Manager, check the following prerequisites:

* A machine on which you plan to install Veeam Backup Enterprise Manager must meet the system requirements. For more information, see [System Requirements](system_requirements.md).
* A user account that you plan to use for installation must have sufficient permissions. For more information, see [Permissions](required_permissions.md).
* Backup infrastructure components communicate with each other over specific ports. These ports must be open. For more information, see [Ports](used_ports.md).
* Local antivirus or antimalware software can interfere with Veeam Backup Enterprise Manager installation. If you receive the Failed to create website 0x80070020 message, disable your local antivirus or antimalware software and run the installation process again. You can re-enable your antivirus software once the installation completes. For more information, see [this Veeam KB article](https://www.veeam.com/kb1992).
* .NET 3.5.1 WCF HTTP Activation Windows component prevents Veeam Backup Enterprise Manager from functioning. Make sure there is no .NET 3.5.1 WCF HTTP Activation Windows component on the Veeam Backup Enterprise Manager server prior to the installation.
* Make sure there is no Microsoft Search Server installed on the machine. If you have Microsoft Search Server, uninstall it prior to the Veeam Backup Enterprise Manager installation.

* If you want to use an already installed PostgreSQL instance for the Enterprise Manager configuration database, make sure the instance can use sufficient resources. For more information, see [Configuring PostgreSQL Instance](#ConfiguringPostgreSQLInstance).
* If you want to use an already installed PostgreSQL instance for the Enterprise Manager configuration database, make sure the instance contains the default postgres database. If you allow the setup to install a new PostgreSQL instance, the postgres database will be created on the instance automatically.

Since Enterprise Manager connects to the postgres database to access the configuration database, do not rename the postgres database upon the Enterprise Manager installation.

* Check the Known Issues section of the [Veeam Backup & Replication Release Notes](https://www.veeam.com/veeam_backup_12_release_notes_rn.pdf).

Configuring PostgreSQL Instance

When you create a new PostgreSQL instance, the default setup is configured to consume a minimum amount of resources, which may not be enough for Enterprise Manager performance.

When installing Veeam Backup Enterprise Manager, you can choose what PostgreSQL instance to use for the Enterprise Manager configuration database. You can use an existing PostgreSQL instance or create a new one.

* If you let the setup create a new PostgreSQL instance, it will be configured automatically.
* If you want to use an existing PostgreSQL instance, make sure that the instance configuration is sufficient for the Enterprise Manager performance.

To adjust the configuration of an existing PostgreSQL instance, take the following steps before you install Enterprise Manager:

1. On a backup server, run the [Set-VBRPSQLDatabaseServerLimits](https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrpsqldatabaseserverlimits.html?ver=13) cmdlet. The cmdlet generates the necessary PostgreSQL configuration and saves it to a dump SQL file.

|  |
| --- |
| Set-VBRPSQLDatabaseServerLimits -OSType <String> -CPUCount <number of CPU cores> -RamGb <RAM in GB> -DumpToFile <file path> |

For example:

|  |
| --- |
| Set-VBRPSQLDatabaseServerLimits -OSType Windows -CPUCount 16 -RamGb 32 -DumpToFile "C:\config.sql" |

1. On the machine with the PostgreSQL instance where you want to deploy the Enterprise Manager configuration database, use the psql tool to apply the configuration from the dump file.

The tool is located in the PostgreSQL installation folder.

|  |
| --- |
| psql -U <user> -f <file path> |

For example:

|  |
| --- |
| psql -U postgres -f "C:\config.sql" |

1. Include the [pg\_stat\_statements](https://www.postgresql.org/docs/current/pgstatstatements.html) library to the PostgreSQL configuration. To add the library, you can manually edit the shared\_preload\_libraries option in the postgres.conf file.

Alternatively, you can do it by by executing the SQL code:

1. Check the content of the shared\_preload\_libraries variable.

|  |
| --- |
| SELECT \* FROM pg\_settings |

1. Add the pg\_stat\_statements library to the shared preloaded libraries.

* If the shared\_preload\_libraries value is empty, assign pg\_stat\_statements to the shared\_preload\_libraries variable.

|  |
| --- |
| ALTER SYSTEM SET shared\_preload\_libraries = pg\_stat\_statements; |

* If the shared\_preload\_libraries value is not empty, add pg\_stat\_statements to the current value separated by comma.

|  |
| --- |
| ALTER SYSTEM SET shared\_preload\_libraries = <existing libraries>, pg\_stat\_statements; |

1. Restart the PostgreSQL service for the new configuration to take effect.
2. Install the pg\_stat\_statements extension. The extension is used to analyze the PostgreSQL performance.

|  |
| --- |
| CREATE EXTENSION IF NOT EXISTS "pg\_stat\_statements"; |

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
