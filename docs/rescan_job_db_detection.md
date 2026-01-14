---
title: "Database Detection"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rescan_job_db_detection.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Database Detection

In this article

After Veeam Plug-In is installed, Plug-In Manager running on the computer collects information about databases on this computer. Plug-In Manager saves collected information to the XML file and sends to Veeam Backup & Replication. The way Plug-In Manager collects information differs depending on the system installed on the computer:

* [Oracle](#oracle)
* [SAP HANA](#sap_hana)
* [SAP on Oracle](#sap_oracle)
* [Microsoft SQL Server](#mssql)

Oracle

On the Oracle server, Plug-In Manager collects information differently depending on the Oracle deployment way:

* If you install Veeam Plug-In on the standalone Oracle server, the rescan process differs depending on the OS running on the target computer:

* In case of Oracle server deployed on the Linux computer, Plug-In Manager scans the oratab or orainventory file. If you use Automatic Storage Management (Oracle ASM), Plug-In Manager rescans both files (oratab and orainventory).
* In case of Oracle server deployed on the Microsoft Windows computer, Plug-In Manager checks Windows Registry and parses services that are running on the computer.

As a result, Veeam Backup & Replication gets 3 levels of the database hierarchy (from top to bottom): hostname, Oracle home, Oracle system identifier (SID).

* If you install Veeam Plug-In on Oracle RAC, Plug-In Manager uses the srvctl utility. With this utility, Plug-In Manager collects information. Plug-In Manager uses, for example, the srvctl config scan and srvctl config database commands.

For Oracle RAC, Plug-In Manager uses a database unique name instead of SID. As a result, Veeam Backup & Replication gets 3 levels of the database hierarchy (from top to bottom): scanname, Oracle home, database unique name.

After rescan completes, you can create an application policy and add any level of the database hierarchy to the scope of this policy. For example, you can add a certain Oracle database or Oracle home that contains several databases.

SAP HANA

On the SAP HANA server, Plug-In Manager collects information depending on the SAP HANA deployment way:

* If you install Veeam Plug-In on the standalone SAP HANA server, Plug-In Manager gets path to the saphostcrl (SAP Host Agent) utility. With this utility, Plug-In Manager gets the list of database instances.

As a result, Veeam Backup & Replication gets 3 levels of the database hierarchy (from top to bottom): hostname, SAP system name, database name.

* If you install Plug-In Manager on the SAP HANA scale-out system, Plug-In Manager collects information from the veeam\_config.xml file.

As a result, Veeam Backup & Replication gets 3 levels of the database hierarchy (from top to bottom): scale-out system name, SAP system name, database name.

|  |
| --- |
| Tip |
| During the Veeam Plug-In deployment on the scale-out system nodes, Veeam Backup & Replication sets the scale-out system name using domain name and SAP system name. If you want to set a custom name, use the --set-scale-out-cluster-name command on the computer side. This custom name will be saved in the veeam\_config.xml file. |

After rescan completes, you can create an application policy and add any level of the database hierarchy to the scope of this policy. For example, you can add a certain SAP HANA database or a host that contains several SAP HANA databases.

SAP on Oracle

On the SAP on Oracle server, Plug-In Manager gets path to the saphostcrl (SAP Host Agent) utility. With this utility, Plug-In Manager gets the list of database instances.

As a result, Veeam Backup & Replication gets 2 levels of the database hierarchy (from top to bottom): hostname, Oracle system identifier (SID).

|  |
| --- |
| Important |
| Veeam Backup & Replication does not support cluster deployment of SAP on Oracle. |

After rescan completes, you can create an application policy and add any level of the database hierarchy to the scope of this policy. For example, you can add a certain Oracle database or a host that contains several Oracle databases.

Microsoft SQL Server

On Microsoft SQL Server, Plug-In Manager collects information about databases and returns collected information to Veeam Backup & Replication server in the .XML format.

If Veeam Plug-In detects SQL Server instances on the machine, connects to each instance and checks if it is a standalone instance or a cluster node. After that, Veeam Plug-In connects to each database and checks if it belongs to an availability group.

As a result, Veeam Backup & Replication gets the following database hierarchy (from top to bottom) depending on the Microsoft SQL Server configuration:

* For standalone servers: server name, instance name, database name.

* For servers in a SQL Server Failover Cluster or Always On Availability Group: cluster or group name, database name.

Page updated 11/28/2025

Page content applies to build 13.0.1.1071
