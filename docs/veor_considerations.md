---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veor_considerations.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

This section lists considerations and known limitations of Veeam Explorer for Oracle.

General

* When Veeam Explorer for Oracle is installed on a server on which both Veeam Backup & Replication and Veeam Backup for Microsoft 365 are installed, the notification settings will be inherited from the Veeam Backup & Replication Global Notification settings.

* Veeam Explorer for Oracle must stay open during all restore, publishing and export operations. If the user who started the operation logs out or is logged out automatically, the operation will be terminated.

This does not apply to instant recovery operations — they are managed by the Veeam Explorers Recovery Service, which runs on the mount server associated with the backup repository.

* [Data recovery to Linux server] You can recover data over SSH only — recovery using Linux Management Agent is not supported.

* [Data recovery to Linux server] Data recovery with Veeam Explorer for Oracle is not supported if the SQL\*Plus environment on the target Oracle server is configured to use glogin.sql or login.sql profile files. For details, see the [Configuring SQL\*Plus](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqpug/configuring-SQL-Plus.html#GUID-D7479120-872F-4E47-AC13-B1B07DF69A46) section of the SQL\*Plus User's Guide and Reference.

* [Data recovery to Linux server] Recovery of databases that resided in an encrypted file system on the original server is not supported. In particular, encrypted LVM volumes are not supported.
* [Data recovery to Microsoft Windows server] Veeam Explorer for Oracle does not support data recovery using a group Managed Service Account (gMSA) to connect to the target server.

* [For Windows machines with ReFS] The mount server, target server, staging server, backup server and the machine where the Veeam Backup & Replication console is installed must support the same or a later ReFS version than that on the source machine. For more information on which OSes support which ReFS version, see [ReFS versions and compatibility matrix](https://gist.github.com/XenoPanther/15d8fad49fbd51c6bd946f2974084ef8#mountability).

* Veeam Explorer for Oracle does not support recovery of encrypted Oracle databases. If you use transparent data encryption (TDE), you can backup and restore your encrypted data with Veeam Plug-In for Oracle RMAN. For more information, see [Oracle Environment Planning](oracle_environment_planning.md#encrypt).
* To recover Oracle data from a restore point containing a shut-down Oracle database, you can use heuristic analysis. In this case, the restore point must be created without application-aware processing. For details, see [Exploring Non-Application Enabled Backups](veor_exploring_nonvss.md).
* After data recovery, auto-start of Oracle databases will be disabled. To enable auto-start of Oracle databases, do the following:

* For Windows machines, set the HKEY\_LOCAL\_MACHINE\SOFTWARE\ORACLE\KEY\_HOMENAME\ORA\_SID\_AUTOSTART registry key value to TRUE.
* For Linux machines, edit the oratab file to contain the following value:

|  |
| --- |
| $ORACLE\_SID:$ORACLE\_HOME:Y |

For example:

|  |
| --- |
| orcl:/u01/app/oracle/product/21.0.0/dbhome\_1:Y |

* Veeam Explorer for Oracle does not support heuristic analysis of backups made with Veeam Agent for Microsoft Windows or Veeam Agent for Linux. If you use a Veeam Agent backup job or policy to back up a shut-down Oracle database, you can restore the Oracle database using Veeam Agent functionality: volume-level restore, file-level restore or bare metal restore.

* Restore, publishing, instant recovery, and export operations of Oracle data from replicas can only recover your data to the latest state of the selected restore point. Replication jobs do not copy Oracle archived logs so data recovery to a point-in-time state is not supported.
* When recovering your Oracle data from CDP replicas, consider the following limitations:

* Restore, publishing, instant recovery, and export operations of Oracle data from CDP replicas can only recover your data to the latest state of the selected long-term restore point. CDP policies do not copy Oracle archived logs so data recovery to a point-in-time state is not supported.

* When you recover your data from CDP replicas, you can only use long-term (both application-consistent and crash-consistent) restore points. Short-term restore points are not supported.
* You can recover your data from a CDP replica if its CDP policy is currently running. During recovery, the CDP policy does not create new long-term restore points and does not delete existing ones. Short-term restore points are still created.
* You cannot restore application items from a CDP replica in parallel with guest OS file restore, SureReplica, and failover.

* Mount of Btrfs and ZFS disks will fail if you want to perform instant recovery, data restore or data publish to the original server. The issue occurs due to a restriction for mounting 2 Btrfs or ZFS disks with identical IDs to the same machine (the Btrfs and ZFS disks have the same IDs on the backup and the original server).

Note that Btrfs volumes on a backed-up Veeam Agent machine must have identifiers in the UUID format in the fstab configuration file.

* Mount operations with [FUSE](https://www.kernel.org/doc/html/latest/filesystems/fuse.html) are not supported on kernel versions 4.0.0 – 4.1.33. Make sure to upgrade the kernel to version 4.1.37 or later.
* Veeam Explorer for Oracle does not support database files containing non-ASCII characters or non-printable ASCII charset symbols that have decimal values from 0 through 31, and 127 in the ASCII table. If the backup contains database files with such characters, the recovery operation will fail.

* Veeam Explorer for Oracle supports SSH fingerprint validation of Linux machines used as target and staging Oracle servers. For more information on how to configure this feature, see [Host Authentication](linux_fingerprint_check.md).

If you have selected the more secure, manual validation in the Veeam Backup & Replication console, consider the following:

* If the target server is unknown or its fingerprint cannot be recognized, you will be able to proceed with the recovery operation after you manually validate the fingerprint in the Veeam Backup & Replication console.
* The validation process matches the fingerprint only with the network identifier of the Linux machine (its IPv4 address, IPv6 address, FQDN, or hostname) used in the respective Veeam Explorer for Oracle session. If you use 2 different network identifiers of the same unverified server in 2 recovery sessions (for example, its IPv4 address in one recovery session and its hostname in another), you will need to perform 2 separate fingerprint validations. No further validations are necessary if you reuse a validated network identifier in another recovery session.

* [For data recovery to Oracle ASM disks] You cannot specify paths and file names for recovered database files. During recovery, Oracle ASM will automatically create and name the necessary files in the specified disk group using the OMF (Oracle Managed Files) feature.
* Veeam Explorer for Oracle does not support recovery of Oracle databases deployed on Solaris OS or IBM AIX. You can restore such databases with Veeam Plug-In for Oracle RMAN. For details, see [Restore to Original Server](restore_rman.md) or [Restore to Another Server](restore_other_server_rman.md).
* [For Linux-based backup servers] All open Explorer sessions become non-responsive after backup server switchover or failback. To continue browsing and restoring your data, you must reopen the sessions.

* [For Linux-based backup servers] To recover Oracle data to a Microsoft Windows server, you must specify a Windows mount server for the backup repository or a default Windows mount server.

Restore from Image-Level Backups

* Veeam Explorer for Oracle does not support restore using PowerShell Direct, VIX API or vSphere Automation API.
* Restore from storage snapshots to the original Oracle server is not supported. To restore your Oracle data from storage snapshots, use the Restore to another server command.
* Point-in-time restore is not supported for backups stored in the DR site by backup copy jobs and for backups stored in a cloud repository. Such repositories cannot be used as a destination location for archived logs.
* Restore of databases from the current restore point is only supported for backups created by Veeam backup job, replication job, VeeamZIP and for imported backup and storage snapshots.

* During restore, temporary files (such as scripts, archive logs and cache files) are created and saved in different locations depending on the operating system of the Oracle machine. Make sure that the volumes where these files are stored have enough free disk space.

* For Windows machines, cache files are stored on the mount server and the remaining temporary files are stored in the C:\Windows\Temp folder of the target server. For more information on how to configure the mount server and the write cache folder, see [Specify Mount Server Settings](repository_mount_server.md).
* For Linux machines, temporary files are stored in the /var/tmp or /tmp folder on the target server, depending on which folder has more free space.

* Veeam Explorer for Oracle does not support data restore, data publishing, instant recovery and export of individual pluggable databases (PDBs) — you can recover entire multitenant container databases (CDBs) that do not contain refreshable PDBs. To restore individual PDBs and CDBs that contain refreshable PDBs, use Veeam Plug-In for Oracle RMAN. For more information, see [Database Recovery](oracle_db_restore.md).
* Before you use Veeam Backup & Replication to back up an Oracle database that was converted from a RAC database to a non-cluster database, make sure to disable all online redo log threads that are managed by other instances. Otherwise, Veeam Explorer for Oracle will not be able to restore the database.
* Restore to ASM disks with 4K sector size is not supported.
* If OS authentication on a target Oracle server is disabled, the restore of databases with enabled ASM will not be possible.
* If OS authentication on a staging Oracle server is disabled, the restore of databases with enabled ASM as of the selected transaction state will not be possible.
* Before restoring a Data Guard to the original location, make sure that the TNS settings are properly configured on the original nodes. For example, check the listener.ora and related configuration files.
* When restoring a Data Guard to another server, individual databases from the Data Guard will be restored as standalone Oracle databases, preserving no Data Guard infrastructure. To restore the Data Guard infrastructure altogether, use either latest state restore, or point-in-time restore.
* Make sure that both the backed-up Oracle machine and the target server to which you are restoring have the same OS patch version.

* Oracle Automatic Storage Management Filter Driver (Oracle ASMFD) is not supported.

Restore from RMAN Plug-in Backups

Restore of Oracle Databases

* Before you restore an Oracle database from an RMAN plug-in backup, make sure that Veeam Plug-In for Oracle RMAN is installed on the target server and properly configured. For more information, see [Deployment and Configuration](rman_plugin_deployment.md).

* Before you restore an Oracle database from an RMAN plug-in backup to another server, make sure that the account used to connect the plug-in on the target server to the backup server and backup repository meets the following requirements:

* The account must either have the Veeam Backup Administrator, or both the Veeam Backup Operator and Veeam Restore Operator roles. You can also use the account under which the backup was created. For more information on how to assign Veeam Backup & Replication roles, see [Managing Users and Roles](users_roles.md).
* The account must have access permissions to the backup repository where the backup is stored. For more information, see [Access and Encryption Settings on Repositories](repository_permissions_rman.md).

If the account does not meet these requirements, you must configure the plug-in on the target server with the credentials of an account that meets the requirements or with a recovery token. You can do this by running the following command on the target server:

|  |
| --- |
| OracleRMANConfigTool --set-auth-data-for-restore |

For more information about this command, see [Restore to Another Server](restore_other_server_rman.md#auth).

* Veeam Explorer for Oracle does not support restore of individual pluggable databases (PDBs) — you can restore entire multitenant container databases (CDBs) that do not contain refreshable PDBs. To restore individual PDBs and CDBs that contain refreshable PDBs, use Veeam Plug-In for Oracle RMAN. For more information, see [Database Recovery](oracle_db_restore.md).
* When restoring to another server with the original name and settings, consider the following:

* The Oracle home and Oracle directory structure must remain the same.
* You must copy the original control file to the target server or recovery catalog of the database which is running in the duplicated cluster. Such a control file must contain information about backups from which the restore is being performed.
* For Oracle ASM, the file system structure of the restored database must remain the same.

* To restore your database with a different name and settings, you must use a server parameter file (SPFILE) for the database and set CONFIGURE CONTROLFILE AUTOBACKUP to ON before backup. For more information, see [Oracle Environment Planning](oracle_environment_planning.md#spfile).

Restore of Oracle Real Application Clusters (RAC)

To restore RAC databases from RMAN plug-in backups, make sure you apply the following restore settings. Otherwise, the databases will be restored as standalone databases.

* Restore to original server: You must restore the database with the original name and settings as on the backup.
* Restore to another server:

* You must restore the database with original name and settings as on the backup.
* The Oracle home and Oracle directory structure must remain the same.
* You must copy the original control file to the target server or recovery catalog of the database which is running in the duplicated cluster. Such a control file must contain information about backups from which the restore is being performed.
* For Oracle ASM, the file system structure of the restored database must remain the same.

When you restore RAC databases to Oracle ASM disks, the ASM instance must be running directly on the target server for the restore operation.

Restore of Data Guard Databases

Data restore with Veeam Explorer for Oracle from backups of Data Guard databases created by Veeam Plug-In for Oracle RMAN has [experimental support](https://www.veeam.com/kb2976). You can restore Data Guard databases from Veeam Plug-in backups with the following limitations:

* Restore to original server:

* You can restore Data Guard primary databases as primary databases only to the original location with the original name and settings.

* You can restore Data Guard standby databases as standby databases only to the original location with the original name and settings.

Restore with different settings will fail due to Data Guard limitations.

* Restore to another server:

* Make sure that the copy of the original cluster already exists in the duplicated environment.

* You must copy the original control file to the target server or recovery catalog of the database which is running in the duplicated cluster. Such a control file must contain information about backups from which the restore is being performed.

* You can restore Data Guard primary databases as primary databases only with the original name and settings.
* You can restore Data Guard standby databases as standby databases only to the original location with original name and settings.

Restore with different settings will fail due to Data Guard limitations.

Publish

* Make sure that the target Oracle server to which you publish your databases is of the same version as the database in the backup.

* Make sure that the volume with the write cache has enough free disk space to store the changes of the published database.

* For Windows machines, the write cache is by default stored in the C:\ProgramData\Veeam\Backup\IRCache\ folder on the mount server. For more information on how to configure the write cache folder, see [Specify Mount Server Settings](repository_mount_server.md).
* For Linux machines, the write cache is stored in the /var/lib/veeam/IRCache folder on the target server.

* If the database that you publish is part of the ASM group, make sure that the target Oracle server also has an ASM group properly configured.

* Publishing the entire Oracle Data Guard is not supported. Individual databases from the Data Guard can be published as standalone Oracle databases, preserving no Data Guard infrastructure.

Instant Recovery

* For Oracle Database 12c, instant recovery is supported starting from version 12.2.0.1.0.211019.
* Instant recovery is supported for image-level backups only. You cannot perform instant recovery from RMAN plug-in backups.
* Make sure that both the backed-up Oracle machine and the target server to which you are restoring have the same OS patch version.
* Instant recovery of the entire Oracle Data Guard is not supported. Individual databases from the Data Guard can be recovered as standalone Oracle databases, preserving no Data Guard infrastructure.
* Instant recovery of SAP on Oracle is not supported.
* If you plan to perform scheduled or manual switchover, make sure that the volume with the write cache has enough free disk space to store the changes of the published database.

* For Windows machines, the write cache is by default stored in the C:\ProgramData\Veeam\Backup\IRCache\ folder of the mount server. For more information on how to configure the write cache folder, see [Specify Mount Server Settings](repository_mount_server.md).
* For Linux machines, the write cache is stored in the /var/lib/veeam/IRCache folder on the target server.

* During the instant recovery process, Veeam Explorer for Oracle requires 512 MB of RAM for each database.
* If you add a new pluggable database to the container during an instant recovery process, the instant recovery session fails.

Export

The databases from the Data Guard are exported as standalone Oracle databases, preserving no Data Guard infrastructure.

Page updated 12/2/2025

Page content applies to build 13.0.1.1071
