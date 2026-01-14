---
title: "Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plan_and_manage_permissions.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Permissions

In this article

To perform database protection and recovery operations on a computer with Veeam Plug-In, you must specify the user whose permissions Veeam Backup & Replication will use to access the protected computer and database management system. Depending on the database system, the specified user accounts must have the permissions listed in this section.

|  |
| --- |
| Note |
| If you plan to restore SAP HANA and Oracle databases using Veeam Explorer for SAP HANA and Veeam Explorer for Oracle, consider the required permissions in the following sections:   * [Permissions for Veeam Explorer for SAP HANA](https://helpcenter.veeam.com/docs/vbr/userguide/vehana_permissions.html?ver=13)  * [Permissions for Veeam Explorer for Oracle](https://helpcenter.veeam.com/docs/vbr/userguide/veo_permissions.html?ver=13) |

Computer with Veeam Plug-In for Oracle RMAN

* The specified user account must belong to the dba system group. The default name of the OSDBA group depends on the operating system:

* dba in Linux and UNIX.
* ORA\_DBA in Microsoft Windows.

To learn more about connecting to a database as administrator using operating system authentication, see [this Oracle article](https://docs.oracle.com/cd/E18283_01/server.112/e17120/dba006.htm#i1006677).

* [For Linux and Unix computers] If you use Oracle ASM and distribute system privileges with separate operating system groups, make sure you follow the Oracle recommendations described in [this Oracle article](https://docs.oracle.com/en/database/oracle/oracle-database/21/ostmg/authenticate-access-asm-instance.html#GUID-5DAEB139-6FAD-4129-A0ED-DF61EDA1B2B8).

* [For Linux and Unix computers] [During application backup policy configuration](policy_oracle_rman_database_processing_general.md), when you specify the OS user account as a database administrator and this OS user account is not the Oracle Software Owner User, make sure one of the following requirements is met:

* Permissions for Oracle directories are set with the chmod command as 775.
* The OS user account has the primary membership in the Oracle Inventory Group (oinstall) group.

To learn how to configure the Oracle Inventory Group, see [this Oracle article](https://docs.oracle.com/en/database/oracle/oracle-database/19/cwlin/example-of-creating-minimal-users-roles-groups.html#GUID-103186A1-74E0-42A8-AC3D-15AF833DCB40).

* [For Microsoft Windows computers] The specified OS user account must have local administrator privileges.

Computer with Veeam Plug-In for SAP HANA

* The OS user must have sufficient privileges to run the HDBSQL command line tool — for example, this can be the <sid>adm user.
* The DB user used for performing backup and recovery operations with system and tenant databases must have the following system privileges:

* BACKUP ADMIN
* CATALOG READ
* DATABASE BACKUP ADMIN

Computer with Veeam Plug-In for SAP on Oracle

The account used for starting Oracle backup and restore processes must be an OS user who owns the data files of the database system. To learn more about logon options, see [this SAP article](https://help.sap.com/doc/saphelp_nw70ehp1/7.01.16/en-US/da/eea6a71c958b4798102ce174d061ac/frameset.htm).

Computer with Veeam Plug-In for Microsoft SQL Server

* If you plan to use the same user account for all Veeam Plug-In operations, this account must be a SQL instance user with a sysadmin role. You can specify this account in the New Protection Group and New Application Backup Policy wizards.

* If you plan to use different user accounts to connect to the machine in the protection group and to start backup and restore processes, these user accounts must have the following permissions:

* The user account responsible for backup and restore processes must be a SQL instance user with the sysadmin role.
* The user account responsible for connections to the machine in the protection group must have the following permissions depending on the backup source:

| Backup Source | Permissions |
| --- | --- |
| Standalone Microsoft SQL instance | public role   * CONNECT SQL * VIEW ANY DATABASE |
| Microsoft SQL failover cluster instance | public role   * CONNECT SQL * VIEW ANY DATABASE * VIEW SERVER PERFORMANCE STATE |
| Always On availability group | public role  and the following permissions:   * CONNECT SQL * VIEW ANY DATABASE * VIEW ANY DEFINITION * VIEW SERVER STATE |

Consider the following:

* Backup or restore operations that use the Microsoft SQL Server Virtual Device Interface (VDI) require that the server connection for SQL Server must be logged on as the sysadmin server role. For details, see [Microsoft SQL documentation](https://learn.microsoft.com/en-us/sql/relational-databases/backup-restore/vdi-reference/reference-virtual-device-interface?view=sql-server-ver15).
* If you work with SQL failover cluster or Always On availability group, you must assign permissions to the account on each node.
* When you install Veeam Plug-In using [Veeam Deployment Kit](protection_group_deployer_service.md), Veeam Plug-In connects to the SQL instance with the NT AUTHORITY\SYSTEM account. To do this, the NT AUTHORITY\SYSTEM account must have a login to connect to the SQL instance. In addition, depending on the backup source, the NT AUTHORITY\SYSTEM account must have at least the permissions listed in the table above.

Page updated 11/28/2025

Page content applies to build 13.0.1.1071
