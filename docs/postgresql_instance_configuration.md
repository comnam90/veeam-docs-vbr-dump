---
title: "Adjusting PostgreSQL Instance Configuration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/postgresql_instance_configuration.html"
last_updated: "10/14/2025"
product_version: "13.0.1.1071"
---

# Adjusting PostgreSQL Instance Configuration


If you selected to use an already installed PostgreSQL instance at the [Specify Database Engine and Instance](install_vbr_sql.md) step of the wizard, make sure that the instance configuration is sufficient for the Veeam Backup & Replication performance.

To adjust the configuration of an existing PostgreSQL instance, take the following steps after you install Veeam Backup & Replication:

1. On a backup server, run the [Set-VBRPSQLDatabaseServerLimits](https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrpsqldatabaseserverlimits.html?ver=13) cmdlet. The cmdlet generates the necessary PostgreSQL configuration and saves it to a dump SQL file.

|  |
| --- |
| Set-VBRPSQLDatabaseServerLimits -OSType <String> -CPUCount <number of CPU cores> -RamGb <RAM in GB> -DumpToFile <file path> |

For example:

|  |
| --- |
| Set-VBRPSQLDatabaseServerLimits -OSType Windows -CPUCount 16 -RamGb 32 -DumpToFile "C:\config.sql" |

1. On the machine with the PostgreSQL instance where you want to deploy the Veeam Backup & Replication configuration database, use the psql tool to apply the configuration from the dump file.

The tool is located in the PostgreSQL installation folder.

|  |
| --- |
| psql -U <user> -f <file path> |

For example:

|  |
| --- |
| psql -U postgres -f "C:\config.sql" |

After you apply the configuration from the dump file, all changes will be written into the postgressql.auto.conf file located in the PostgreSQL installation folder. This file is loaded when the service starts and takes precedence over the default PostgreSQL configuration file.

1. Include the [pg\_stat\_statements](https://www.postgresql.org/docs/current/pgstatstatements.html) library to the PostgreSQL configuration. To add the library, you can manually edit the shared\_preload\_libraries option in the postgresql.conf file.

Alternatively, you can do it by executing the SQL code:

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


