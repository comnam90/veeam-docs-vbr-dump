---
title: "Backup of Database Systems"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_backup_linux_dbs_processing.html"
last_updated: "11/28/2025"
product_version: "13.0.1.1071"
---

# Backup of Database Systems

In this article

You can instruct Veeam Agent for Linux to create consistent backups of Veeam Agent computers that run one of the supported database systems using application-aware processing..

Supported Database Systems

* MySQL
* Oracle

Veeam Agent processes the Oracle database system using internal components: oralib and oracleproxy.

* PostgreSQL

Veeam Agent processes the PostgreSQL database system using an internal component: pgsqlagent.

To learn how processing of database systems works, see the [Backup of Database Systems](https://helpcenter.veeam.com/docs/agentforlinux/userguide/database_processing.html?ver=13) section in the Veeam Agent for Linux User Guide.

Backup of Database Archived Logs

If you back up the Oracle or PostgreSQL database system using a backup job managed by Veeam backup server, Veeam Backup & Replication can also back up archived logs. You can use archived logs to restore the database system to the necessary state up to the certain operation. Veeam Backup & Replication backs up archived logs in the similar way as in a backup job for VMs, with the same requirements and limitations.

To learn more about backup of Oracle database archived logs, see [Oracle Log Backup](oracle_backup.md).

To learn more about backup of PostgreSQL database archived logs, see [PostgreSQL Log Backup](postgresql_backup.md).

Considerations and Limitations

Consider the following about application-aware and database processing:

* Nosnap Veeam Agent for Linux and nosnap Veeam Agent for Linux on Power do not support application-aware processing and cannot be used to back up database systems.
* Application-aware processing and database processing options are available if you have selected the Server option at the [Job Mode](agent_job_protection_linux.md) step of the wizard.
* Application-aware processing and database processing options are available if you have selected the Entire computer or Volume level backup option at the [Backup Mode](agent_job_mode_linux.md) step of the wizard.

* If there are multiple database systems on the Veeam Agent computer, consider the following:

* Veeam Agent supports processing of multiple PostgreSQL or Oracle database systems on one Veeam Agent computer.
* Veeam Agent does not support processing of multiple MySQL database systems on one Veeam Agent computer.
* Veeam Agent does not support processing of multiple database systems of different types on one Veeam Agent computer.

* Veeam Agent does not support 32-bit database systems installed on a 64-bit Linux OS.

* Available script settings depend on the options that you have selected at the [Job Mode](agent_job_protection_linux.md) and [Backup Mode](agent_job_mode_linux.md) steps of the wizard. To learn more, see [Backup Job and Snapshot Scripts](agent_job_guest_scripts.md).

Requirements and Limitations of MySQL Processing

* Veeam Agent for Linux supports processing of MySQL database systems version 5.7 – 9.0.

* Configurations with multiple MySQL installations or instances on the same machine are not supported.
* MySQL Cluster versions are not supported.
* MySQL tables that use the MyISAM storage engine must be locked to keep them in consistent state while Veeam Agent is creating the system snapshot. To correctly process such tables, MySQL account must have the following instance-wide privileges:

* SELECT. This privilege enables Veeam Agent to access tables' metadata and select for a lock the tables that use the MyISAM storage engine. Without this privilege, the processing of the MySQL database system will run successfully but MyISAM tables will not be locked, which may result in an inconsistent state of the backed up data.
* LOCK TABLES. This privilege is required for locking the selected MyISAM tables. If some MyISAM tables are selected but the MySQL account does not have the LOCK TABLES privilege, the processing of the MySQL database system will fail.
* RELOAD or FLUSH\_TABLES. If some MyISAM tables are selected but the MySQL account does not have either RELOAD or FLUSH\_TABLES privilege, the processing of the MySQL database system will fail.

To obtain information about the privileges that are assigned to an account, use MySQL functionality, for example, the SHOW GRANTS statement. To learn more, see [MySQL documentation](https://dev.mysql.com/doc/refman/8.0/en/show-grants.html).

Requirements and Limitations for Oracle Processing

* Oracle Database versions 11g – 21c are supported for all operating systems supported by Veeam Agent for Linux. To learn more, see [System Requirements](system_requirements.md#OS).
* Automatic Storage Management (ASM) is not supported.

* Oracle Real Application Clusters (RAC) are not supported.

* Oracle Grid Infrastructure is not supported.

* Oracle Database Express Edition (XE) is not supported.

* SAP on Oracle is not supported.

* Oracle Database architectures with Data Guard are not supported.

Requirements and Limitations for PostgreSQL Processing

* Veeam Agent supports processing of PostgreSQL database systems version 13 – 18.

* Veeam Agent does not support backup of PostgreSQL clusters.

* Veeam Agent does not support high availability cluster configurations and replication setups of PostgreSQL servers.

* In PostgreSQL 15 and earlier, Veeam Agent does not support configuration sub-files that are specified in the include, include\_dir and include\_if\_exist options in the postgresql.conf file. All PostgreSQL configurations, instance ports in particular, must be specified in the single postgresql.conf file.

Starting from PostgreSQL 16, the pg\_hba.conf and pg\_ident.conf files can also have configuration sub-files specified in the include, include\_dir and include\_if\_exist options. Veeam Agent does not support these configuration sub-files either. Make sure that in PostgreSQL 16 and later all configurations are specified only in the postgresql.conf, pg\_hba.conf and pg\_ident.conf files.

Related Topics

* [MySQL Processing Settings](agent_job_guest_mysql.md)
* [Oracle Processing Settings](agent_job_guest_oracle.md)
* [PostgreSQL Processing Settings](agent_job_guest_postgresql.md)

Page updated 11/28/2025

Page content applies to build 13.0.1.1071
