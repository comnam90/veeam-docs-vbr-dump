---
title: "Using Veeam Configuration Database Connection Utility in Veeam Backup & Replication for Linux"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/dbconfig_utility_linux.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Using Veeam Configuration Database Connection Utility in Veeam Backup & Replication for Linux

In this article

The utility is located on the backup server by the following path: /opt/veeam/vbr/Veeam.Backup.Setup.Linux.dll. To use the utility, you must have root permissions on the local machine.

To manage connection settings for Veeam Backup & Replication, check [prerequisites](#dbconfig_linux_byb) and perform the following steps:

1. [Open Shell](#dbconfig_linux_step1).
2. [Run the Utility](#dbconfig_linux_step2).
3. [Finalize the Connection Process](#dbconfig_linux_step3).

Limitations and Considerations

Before you configure database connection settings, consider the following:

* You must manually stop the Veeam Backup & Replication services before using the utility.
* If you change the database to which Veeam Backup & Replication must be connected, make sure that the database to which Veeam Backup & Replication is currently connected is available. If not, you must stop the Veeam Backup Service on the machine where Veeam Backup & Replication is installed.

* Do not connect Veeam Backup & Replication to the database which is being used by another Veeam Backup & Replication. In that case, Veeam Backup & Replication will not be able to utilize the encrypted data stored in this database.
* Both local and remote PostgreSQL instances are supported. If a database with the specified name does not exist on the selected PostgreSQL instance, it will be created anew.
* The configuration database connection utility supports only connection to configuration databases of the current version.

Step 1. Open Shell

To open Shell, do the following:

1. Log into host management console.
2. Click Remote Access Configuration.
3. Click Enter Shell.

Step 2. Run the Utility

In Shell, run the following command and specify all parameter values:

|  |
| --- |
| VEEAM\_SETUP\_PGSQL\_PASSWORD=qwerty dotnet /opt/veeam/vbr/Veeam.Backup.Setup.Linux.dll backupdbconfigurator /sqlservername:192.168.100.50 /sqlserverport:5432 /sqlserverdatabasename:VeeamDB /sqlserverlogin:postgres |

Perform the following steps:

1. Specify the VEEAM\_SETUP\_PGSQL\_PASSWORD environment variable value.
2. Use dotnet to run the Veeam.Backup.Setup.Linux.dll file.
3. Specify the path to Veeam.Backup.Setup.Linux.dll file.
4. Enter the backupdbconfigurator command and specify the sqlservername, sqlserverport, sqlserverdatabasename and sqlserverlogin parameter values.

Utility Parameters

| Parameter | Description | Required |
| --- | --- | --- |
| VEEAM\_SETUP\_PGSQL\_PASSWORD | Specifies the password for the database that Veeam Backup & Replication will use. | Yes |
| sqlservername | Specifies the PostgreSQL server name.  Supported values: hostname\IP address. | Yes |
| sqlserverport | Specifies the PostgreSQL server port. | Yes |
| sqlserverdatabasename | Specifies the PostgreSQL database name. | Yes |
| sqlserverlogin | Specifies the login name for the PostgreSQL database. | Yes |

Step 3. Finalize the Connection Process.

After new settings are applied, manually start the Veeam Backup & Replication services again.

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
