---
title: "Oracle Environment Planning"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/oracle_environment_planning.html"
last_updated: "6/15/2026"
product_version: "13.0.2.29"
---

# Oracle Environment Planning


Before you deploy Veeam Plug-In, consider the following requirements and limitations.

Installation Prerequisites

On machines running Linux or Unix OS, consider the following prerequisites:

* Before you install Veeam Plug-In, make sure that the /opt/veeam directory is writable.
* Before you configure Veeam Plug-In, make sure that the NOEXEC mount option is disabled for the /var and /tmp directories.

Data Channel Allocation

Oracle Standard Edition supports only one data channel. Oracle Enterprise Edition supports multiple parallel channels. You can configure parallel channels in the Veeam Plug-In configuration wizard or by using the ALLOCATE CHANNEL command in RMAN scripts. For more information, see [Configuring Veeam Plug-In for Oracle RMAN](configuring_rman_plugin.md) or [Oracle RMAN Channel Allocation](rman_allocation_backup.md).

Scheduling

You can schedule backup processes with all Oracle RMAN relevant scheduling options like Cron, Windows Task Scheduler, UC4 and TWS.

If you use Veeam Backup & Replication or Veeam Agents to create image-level backups of the Oracle server, you can schedule the backup job and run Oracle RMAN backup scripts along with the backup job. For detailed instructions on how to add Oracle RMAN scripts to a backup job, see one of the following guides:

* For Veeam Backup & Replication: [Pre-Freeze and Post-Thaw Scripts](backup_job_vss_scripts_vm.md).
* For Veeam Agent for Windows: [Pre-Freeze and Post-Thaw Scripts](https://helpcenter.veeam.com/docs/agentforwindows/userguide/backup_job_vss_scripts.html?ver=60) section of the Veeam Agent for Windows User Guide.
* For Veeam Agent for Linux: [Pre-Freeze and Post-Thaw Scripts](https://helpcenter.veeam.com/docs/agentforlinux/userguide/backup_job_script.html?ver=60#snapshot) section of the Veeam Agent for Linux User Guide.

|  |
| --- |
| Note |
| If you want to use Oracle RMAN scripts within backup jobs of Veeam Backup & Replication or Veeam Agents, consider the following:   * A backup job does not control the workflow of Oracle RMAN scripts. The backup job invokes the script and gets an exit status when the script is finished. Backup job logs show if the script was executed successfully. The script is considered to be executed successfully if the return is "0". To see if the script failed, configure the script to return the exit status different than "0" in case of any errors. * The default timeout for a custom script in a backup job is 10 minutes. If the script runs longer than the default time, consider submitting a support case on the [Veeam Customer Support Portal](https://www.veeam.com/support.html). |

Oracle Temporary Tablespace

Veeam Plug-In runs SQL queries on the Oracle database to collect statistical information about the RMAN job processes. Based on availability of hardware resources, the Oracle server uses an allocated Oracle Temporary Tablespace to store the SQL queries.

To avoid lack of storage in the temporary tablespace, configure the Oracle Temporary Tablespace resources. For more information about creating and managing tablespaces, see [this Oracle article](https://docs.oracle.com/cd/A97630_01/server.920/a96540/statements_75a.htm).

Oracle Cluster Solutions

Veeam Plug-In for Oracle RMAN supports backup and restore of Oracle databases that operate in clusters based on one of the following solutions:

Oracle Cluster Solutions

| Solution | Standalone Mode | Managed Mode |
| Oracle Exadata, Oracle Database Appliance, Oracle RAC | Supported | Supported |
| Oracle Data Guard | Supported | Not supported |

To learn more about operation modes, see [Standalone and Managed Operations Modes](overview_operation_modes.md).

Before you back up the cluster, review considerations and limitations in [Support for Cluster Solutions](oracle_rman_overview_clusters.md).

Oracle Backup Encryption

The Oracle Secure Backup SBT library supports RMAN encrypted backups. Veeam Plug-In does not support encrypted backups of Oracle databases.

If the backup encryption is enabled, Veeam Plug-In backup jobs fail with the following error: ORA-19919: encrypted backups to tertiary storage require Oracle Secure Backup. For more information about how you can disable the backup encryption to avoid this error, see [this Oracle article](https://docs.oracle.com/database/121/BRADV/rcmconfa.htm#GUID-BAA3CFF0-C95C-4AF2-90DD-764754325D73).

Alternatively, you can use transparent data encryption (TDE) provided by Oracle. Using TDE, you can encrypt database data with an encryption key, back up encrypted data with Veeam Plug-In, then restore data with Veeam Plug-In and decrypt using the same encryption key. Restore with Veeam Explorer for Oracle is not supported for this scenario. To learn more about Oracle TDE encryption, see [this Oracle article](https://nam10.safelinks.protection.outlook.com/?url=https://docs.oracle.com/en/database/oracle/oracle-database/21/asoag/introduction-to-transparent-data-encryption.html&data=05|02|Andrey.Vityuk@veeam.com|fe3688d966ef489f4bcb08dcb31f7405|ba07baab431b49edadd7cbc3542f5140|1|0|638582194874572718|Unknown|TWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0=|0|||&sdata=dwNLM2aa6C51pgaekWaPq1mCOVu5zPiMoVqpF3ps4P4=&reserved=0).

Naming of Database Files

Veeam Plug-In for Oracle RMAN does not support non-printable ASCII charset symbols that have decimal values from 0 through 31, and 127 in ASCII table. If Veeam Plug-In processes a database file with one of the mentioned symbols, the backup operation finishes with an error.

Naming of Backup File

During backup and restore operations, Veeam Plug-In uses the repositoryID parameter from the Veeam Plug-In configuration file. In the Veeam Plug-In configuration file, the repository ID is stored in the following format: repositoryID=“xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx”.

Before selecting multiple backup repositories for naming, consider the following:

* If you select multiple Veeam backup repositories and enable RMAN copy processing, you must use the repository ID with the “/” sign as a prefix for the backup file names:

|  |
| --- |
| /.vab |

where:

* <repository\_id> is the repository ID.
* <backup\_file\_name> is the name of the backup file.

For example:

|  |
| --- |
| CONFIGURE CHANNEL DEVICE TYPE SBT\_TAPE PARMS 'SBT\_LIBRARY=/opt/veeam/VeeamPluginforOracleRMAN/libOracleRMANPlugin.so' FORMAT '3ff6897d-5107-408e-a176-68bf8c8ff3a4/RMAN\_%I\_%d\_%T\_%U.vab'; CONFIGURE CONTROLFILE AUTOBACKUP FORMAT FOR DEVICE TYPE SBT\_TAPE TO '%F\_RMAN\_AUTOBACKUP.vab'; |

This allows RMAN to directly access the requested backup file on one of the copy extents.

* If you select multiple Veeam backup repositories and disable RMAN copy processing, backup files will be read by default from the first selected repository.

|  |
| --- |
| Important |
| In a backup file name, you cannot use the following characters, which are reserved by Microsoft Windows: < > : " / \ | ? \* and some others. To learn more about file naming conventions, see [this Microsoft article](https://learn.microsoft.com/en-us/windows/win32/fileio/naming-a-file#naming-conventions). |

Backup of Control File and SPFILE

If you set CONFIGURE CONTROLFILE AUTOBACKUP option to ON, after you run the BACKUP command, RMAN will automatically create a control file and an SPFILE backup. For details about backing up the RMAN control file, see [this Oracle article](https://docs.oracle.com/en/database/oracle/oracle-database/21/racad/configuring-recovery-manager-and-archiving.html#GUID-7A1758E4-DEF2-422F-BBEA-34826DFF03FE).

Controlfile Autobackup File Naming

When using the CONTROLFILE AUTOBACKUP option, consider the following for autobackup files naming:

* If you perform a restore operation with Veeam Explorer for Oracle using a different database name and database settings, you must enable the autobackup of the control file.

If you use the CONTROLFILE AUTOBACKUP option, the Veeam Plug-In configuration wizard creates the following RMAN configuration entry:

|  |
| --- |
| CONFIGURE CONTROLFILE AUTOBACKUP FORMAT FOR DEVICE TYPE SBT\_TAPE TO '%F\_RMAN\_AUTOBACKUP.vab'; |

* If after configuring Veeam Plug-In you enable the CONTROLFILE AUTOBACKUP option, you must start the configuration wizard again. The control file backup naming option will be set to default.
* If you enable the CONTROLFILE AUTOBACKUP option in a standalone server or a Oracle cluster node, RMAN will create autobackup files with the same names for databases with the same database ID (DBID). This can cause Veeam Plug-In operation errors.

To avoid errors, you must provide unique names for individual databases. See the following example about how to add a unique identifier to the database using the db\_unique\_name parameter.

|  |
| --- |
| CONFIGURE CONTROLFILE AUTOBACKUP FORMAT FOR DEVICE TYPE SBT\_TAPE TO '%F\_ORCLUNIQNAME\_RMAN\_AUTOBACKUP.vab'; |

Parallel Processing for Backup Repositories

Veeam Plug-In supports parallel backup processing for up to 4 backup repositories or scale-out backup repositories. In the plug-in configuration wizard, if you select more than one repository, the parallelism functionality will be enabled automatically.

|  |
| --- |
| Note |
| RMAN parallel processing must be enabled for Oracle Enterprise Edition. |

Additional Files to Back Up

Veeam Plug-In creates backups of databases and logs. Apart from these files,

Oracle Home

* It is recommended to back up the Oracle home folder in addition to RMAN backups. You can back it up with Veeam Backup & Replication or Veeam Agents.
* If the Oracle home folder is on a shared disk, you can use the file-level backup functionality of Veeam Backup & Replication or Veeam Agent for Linux. Alternatively, you can copy the Oracle home folder to a non-shared disk before the backup.

Oracle Recovery Catalog

You can back up the Oracle Recovery Catalog with Veeam Plug-In on the Recovery Catalog server according to the Oracle procedures. For details, see [this Oracle article](https://docs.oracle.com/cd/E11882_01/backup.112/e10642/rcmcatdb.htm#BRADV8015).

Veeam Plug-In for RMAN Configuration File

You can back up the Veeam Plug-In configuration file. The file is located in the following directories:

* [Linux or Unix]: /opt/veeam/VeeamPluginforOracleRMAN/veeam\_config.xml

* [Windows]: %PROGRAMFILES%\Veeam\VeeamPluginforOracleRMAN\veeam\_config.xml

|  |
| --- |
| Note |
| You can also create an image-level backup of the Oracle server using the image-level backup functionality of Veeam Backup & Replication or Veeam Agents. |

Disabling Veeam Explorer Processing

You can disable Veeam Explorer for Oracle based restore for specific Oracle servers. To disable the restore on the Veeam Explorer for Oracle side, do the following:

* [Linux or Unix] On the Oracle server, log in as a user with the Oracle Administrator rights and create an empty file in the following directory: /etc/veeam/disablerestore
* [Windows] On the Oracle server, create an empty file in the following directory: %ProgramData%\Veeam\disablerestore

Database Recovery

Before you recover your database using Veeam Explorer for Oracle, consider the following:

* The database that you want to restore must use SPFILE. If SPFILE is not used, a warning will be displayed during the Veeam Plug-In configuration.
* If you use huge pages, make sure that you allocated enough memory to the system where you want to restore your database.


