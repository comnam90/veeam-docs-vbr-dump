---
title: "Starting Backup Job on Veeam Plug-In Side"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/manage_policy_start_job_from_vp.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Starting Backup Job on Veeam Plug-In Side

In this article

In the Veeam Plug-In management scenario, you can still manually start an application backup job from the computer with Veeam Plug-In installed. For example, this may be useful if you want to create an ad-hoc backup just before the database maintenance.

Keep in mind the following:

* You can back up only those databases that are added to the application backup policy on the Veeam Backup & Replication side. If the database is not added to any application backup policy, you cannot back up this database from the computer with Veeam Plug-In.

* You cannot start an application backup job from the computer with Veeam Plug-In installed, if the application backup policy on the Veeam Backup & Replication side is in the disabled state. To learn how to enable a disabled backup policy, see [Enabling and Disabling Backup Policy](manage_policy_disable.md).

* When you start an application backup job from the computer with Veeam Plug-In installed, Veeam Backup & Replication will not start the application backup policy. The policy will stay in the idle state.

The way you configure and start the backup job depends on the Veeam Plug-In you work with:

* [Veeam Plug-In for Oracle RMAN](#op)
* [Veeam Plug-In for SAP HANA](#sh)
* [Veeam Plug-In for SAP on Oracle](#so)
* [Veeam Plug-In for Microsoft SQL Server](#mssql)

Veeam Plug-In for Oracle RMAN

If you create an application backup policy for Veeam Plug-In for Oracle RMAN, Veeam Backup & Replication does not save the backup job configuration on the computer with Veeam Plug-In. As a result, you can configure and start the backup job as a command in the Oracle RMAN console.

Consider that the command differs depending on the OS running on the computer with Veeam Plug-In for Oracle RMAN installed:

* Example for Windows-based computers:

|  |
| --- |
| RUN { |

* Example for Linux- or Unix-based computers:

|  |
| --- |
| RUN {   ALLOCATE CHANNEL VeeamAgentChannel1  DEVICE TYPE SBT\_TAPE PARMS 'SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so' FORMAT 'RMAN\_%I\_%d\_%T\_%U.vab'; BACKUP INCREMENTAL LEVEL 0 DATABASE; } EXIT; |

|  |
| --- |
| Important |
| If you selected the database authentication method during the application backup policy configuration, the backup operation started from the computer with Veeam Plug-In will fail. This happens because the database credentials are not available on the computer with Veeam Plug-In. Veeam Backup & Replication stores the database credentials only in the application backup policy settings. For details, see [Authentication Against Database](rman_auth_methods.md).  As a workaround, you can manually set the database credentials on the computer with Veeam Plug-In using the OracleRMANConfigTool tool. The command to manually set the database credentials differs depending on the OS of the machine where Veeam Plug-In is installed:   * On machines running Linux or Unix OS: OracleRMANConfigTool --set-db-credentials * On machines running Windows OS:  1. On the Oracle server, go to %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN. 2. Run the required OracleRMANConfigTool.exe --set-db-credentials command.   The database credentials that you specified with the tool will be saved in the Veeam Plug-In configuration file (veeam\_config.xml). Veeam Plug-In will use them for backup operations started from the computer with Veeam Plug-In. |

Veeam Plug-In for SAP HANA

If you create an application backup policy for Veeam Plug-In for SAP HANA, Veeam Backup & Replication saves the backup job parameters in the SAP HANA global.ini file on the computer with Veeam Plug-In. As a result, you can use SQL commands or SAP HANA tools to back up SAP HANA databases. To learn more, see [Database Protection](sap_hana_backup.md).

Veeam Plug-In for SAP on Oracle

If you create an application backup policy for Veeam Plug-In for SAP on Oracle, Veeam Backup & Replication saves the backup job configuration on the computer with Veeam Plug-In. Depending on the version of Oracle Database, Veeam Plug-In stores the configuration file in one of the following directories:

* For Oracle 12 and later, the configuration file is stored at SAPDATA\_HOME/sapprof.
* For Oracle 11, the configuration file is stored at ORACLE\_HOME/dbs.

The BRBACKUP tool can use this configuration file as an initialization profile. As a result, you can use this file to start the backup operation from the Veeam Plug-In side. To learn more about configuration file, see [Configuring Plug-In for SAP on Oracle](configure_sap_orcl.md).

Veeam Plug-In for Microsoft SQL Server

If you create an application backup policy for Veeam Plug-In for Microsoft SQL Server, Veeam Backup & Replication does not save the backup job configuration on the computer with Veeam Plug-In. As a result, you can start an application backup policy in the Back Up Database wizard or Command-Line Interface. To learn more, see [Performing Backup](mssql_protection.md).

|  |
| --- |
| Tip |
| With Veeam Plug-In for Microsoft SQL Server operating in the managed mode, you can still back up an SQL database using a standalone backup job. For details, see [Backing Up SQL Databases with Standalone Backup Job](mssql_configure_backup_exclude_from_managed.md). |

Page updated 11/28/2025

Page content applies to build 13.0.1.1071
