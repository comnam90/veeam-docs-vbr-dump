---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_considerations.html"
last_updated: "2/9/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


This section lists considerations and known limitations of Veeam Explorer for Microsoft SQL Server.

General

* When Veeam Explorer for Microsoft SQL Server is installed on a server on which both Veeam Backup & Replication and Veeam Backup for Microsoft 365 are installed, the notification settings will be inherited from the Veeam Backup & Replication Global Notification settings.

* Veeam Explorer for Microsoft SQL Server must stay open during all restore, publishing and export operations. If the user who started the operation logs out or is logged out automatically, the operation will be terminated.

This does not apply to restore from Veeam Plug-In for Microsoft SQL Server and instant recovery operations — they are managed by the Veeam Explorers Recovery Service, which runs on the mount server associated with the backup repository.

* To restore, publish and instantly recover your Microsoft SQL Server data without granting access to the administrative share, make sure that the Veeam Installer Service is installed on the target server. For more information on installing this service, see [Veeam Installer Service](installer_service.md).
* Restore, publishing, instant recovery, and export operations of Microsoft SQL Server data from replicas can only recover your data to the latest state of the selected restore point. Replication jobs do not copy Microsoft SQL Server transaction logs so data recovery to a point-in-time state is not supported.

* When recovering your Microsoft SQL Server data from CDP replicas, consider the following limitations:

* Restore, publishing, instant recovery, and export operations of Microsoft SQL Server data from CDP replicas can only recover your data to the latest state of the selected long-term restore point. CDP policies do not copy Microsoft SQL Server transaction logs so data recovery to a point-in-time state is not supported.
* When you recover your data from CDP replicas, you can only use long-term (both application-consistent and crash-consistent) restore points. Short-term restore points are not supported.
* You can recover your data from a CDP replica if its CDP policy is currently running. During recovery, the CDP policy does not create new long-term restore points and does not delete existing ones. Short-term restore points are still created.
* You cannot restore application items from a CDP replica in parallel with guest OS file restore, SureReplica, and failover.

* When using image-level backups, Veeam Explorer for Microsoft SQL Server does show or support recovery of system databases (master, model, msdb). To recover system databases from image-level backups, use guest OS file restore. For more information, see [Guest OS File Restore](guest_file_recovery.md). Note that you can explore and restore these databases with Veeam Explorer for Microsoft SQL Server from backups created with Veeam Plug-In for Microsoft SQL Server.
* To connect to machines with Microsoft SQL Server that are running Microsoft OLE DB Driver 19 and operating in the Strict encryption mode, go to the necessary Veeam Explorer for Microsoft SQL Server Config.xml file and add the following XML code:

|  |
| --- |
| <Veeam>     <SQLCore StrictSQLConnectionEncryption="True"/>  </Veeam> |

The Config.xml files are located on the machine where Veeam Explorer for Microsoft SQL Server is running.

* The user configuration file is located in the %UserProfile%\AppData\Local\Veeam\Backup\SQLExplorer directory.
* The global configuration file is located in the %ProgramData%\Veeam\Backup\SQLExplorer directory.

If a configuration file named Config.xml does not exist in the necessary directory, create this file.

* Veeam Explorer for Microsoft SQL Server does not support data recovery using a group Managed Service Account (gMSA) to connect to the target server.
* [For Linux-based backup servers] To recover Microsoft SQL Server data, you must specify a Windows mount server for the backup repository or a default Windows mount server.
* By default, the AUTO\_CLOSE option for Microsoft SQL Server databases is set to False. If AUTO\_CLOSE is enabled, your databases may be skipped from processing.
* [For machines with ReFS] The mount server, target server, staging server, backup server and the machine where the Veeam Backup & Replication console is installed must support the same or a later ReFS version than that on the source machine. For more information on which OSes support which ReFS version, see [ReFS versions and compatibility matrix](https://gist.github.com/XenoPanther/15d8fad49fbd51c6bd946f2974084ef8#mountability).
* [For Linux-based backup servers] All open Explorer sessions become non-responsive after backup server switchover or failback. To continue browsing and restoring your data, you must reopen the sessions.

Restore from Image-Level Backups

* Veeam Explorer for Microsoft SQL Server does not support restore using PowerShell Direct, VIX API or vSphere Automation API.
* Table-level restore (with the Restore Database Schema and Data option) is not supported for the following types of tables:

* Tables with external dependencies, such as tables extended to Microsoft Entra using the Stretch Database functionality.
* System-versioned temporal tables.

To restore these types of tables, use full database restore.

* The Replace logic is not supported when restoring schema objects.
* To restore an encrypted database, consider reading [this Veeam Knowledge Base article](https://www.veeam.com/kb2006).
* Before you restore a Microsoft SQL Server database to an Always On availability group, make sure that Veeam Explorer for Microsoft SQL Server can access all nodes in the availability group.

* To restore a database from an Always On availability group node as of the selected transaction state, the nodes of such a group must be in the same time zone.
* Databases located on disks excluded from backup are displayed in Veeam Explorer for Microsoft SQL Server with a question mark next to each database. It is not possible to restore data of such databases. For more information, see [this Veeam KB article](https://www.veeam.com/kb2788).

Restore from Plug-in Backups

* Before you restore a database from a SQL plug-in backup, make sure that Veeam Plug-In for Microsoft SQL Server is installed on the target server and properly configured. For more information, see [Deployment and Configuration](mssql_plugin_deployment.md).

* Before you restore a database from a SQL plug-in backup to another server, make sure that the account used to connect the plug-in on the target server to the backup server and backup repository meets the following requirements:

* The account must either have the Veeam Backup Administrator, or both the Veeam Backup Operator and Veeam Restore Operator roles. You can also use the account under which the backup was created. For more information on how to assign Veeam Backup & Replication roles, see [Managing Users and Roles](users_roles.md).
* The account must have access permissions to the backup repository where the backup is stored. For more information, see [Access and Encryption Settings on Backup Repositories](repository_permissions_mssql.md).

* Microsoft SQL Server does not support transaction log backups for the master database. Because of this, you can only restore the master database as a single database, from a full backup, to the latest state on the backup file and with the default (RECOVERY) restore option.

* Consider the following before restoring databases from SQL plug-in backups of Always On availability groups:

* Veeam Explorer for Microsoft SQL Server will restore the database as a standalone database. To recreate the original Always On architecture, you must manually add the database to the Always On availability group. For details, see [Restore of Always On Availability Groups](mssql_plugin_aon.md#aon_restore).
* The Restore Latest State and Restore to a Point-in-Time State options are not available — you can only use the Restore to Another Server option, even when restoring to the original server. Veeam Explorer for Microsoft SQL Server cannot determine the original Always On availability group and always requires the target server connection parameters.

* When restoring data from SQL plug-in backups, you cannot use the Strict encryption mode to connect to the target server. You can use the Mandatory or Optional encryption modes instead.

* To use the Mandatory encryption mode, you must go to the necessary Veeam Explorer for Microsoft SQL Server Config.xml file and add the following XML code:

|  |
| --- |
| <Veeam>     <SQLCore EncryptionType="Mandatory"/>  </Veeam> |

The Config.xml files are located on the machine where Veeam Explorer for Microsoft SQL Server is running.

* The user configuration file is located in the %UserProfile%\AppData\Local\Veeam\Backup\SQLExplorer directory.
* The global configuration file is located in the %ProgramData%\Veeam\Backup\SQLExplorer directory.

If a configuration file named Config.xml does not exist in the necessary directory, create this file.

Note that when using the Mandatory encryption mode you must manually add the certificate generated by Microsoft SQL Server on the target server to the certificate store of the mount server associated with the backup repository.

* To use the Optional encryption mode, no additional configuration is necessary.

Publishing

* Publishing to a Microsoft SQL Server failover cluster requires a free drive letter on each cluster node to mount a volume from the backup. If the backed-up machine has multiple volumes, a free drive letter must be available for each volume in the backup. For more information, see [How Publishing Works](vesql_how_publishing_works.md).
* You can publish the same database more than once.

* Make sure that the mount server volume with the write cache has enough free disk space to store the changes of the published database. By default, the write cache is stored in the C:\ProgramData\Veeam\Backup\IRCache\ folder of the mount server. For more information on how to configure the write cache folder, see [Specify Mount Server Settings](repository_mount_server.md).

* After you unpublish a database, Veeam Explorer for Microsoft SQL Server detaches such a database from the target Microsoft SQL Server machine but the restore point will continue to remain on the target machine for the next 15 minutes.
* If a Veeam Explorer for Microsoft SQL Server session has been terminated in any way other than by clicking Exit in the main menu (or by clicking the X button in the upper-right corner), then all the published databases will continue to remain attached to the target Microsoft SQL Server machine with the Recovery pending state.
* If published databases have been renamed manually using SQL tools (for example, Microsoft SQL Management Studio), Veeam Explorer for Microsoft SQL Server will not be able to unpublish such databases properly. In this case, all the renamed databases will continue to remain attached to the target Microsoft SQL Server machine and you will have to remove them manually using SQL tools.
* Veeam Explorer for Microsoft SQL Server does not back up published databases.

* Upon closing the Veeam Explorer for Microsoft SQL Server console, all the published databases will be detached from the target Microsoft SQL Server instance automatically. Mount points will be also dismounted from under the C:\VeeamFLR directory.

Instant Recovery

* To restore an encrypted database, consider reading [this Veeam Knowledge Base article](https://www.veeam.com/kb2006).

* If you perform instant recovery of a database from an Always On availability group node, Veeam Explorer for Microsoft SQL Server will restore it as a standalone database.
* For desktop versions of Microsoft Windows (7, 8, 8.1, 10), you must perform instant recovery of multiple databases one by one. The limitation occurs because desktop versions of Microsoft Windows OS do not allow more than 20 incoming concurrent TCP/IP connections. For details, see [Microsoft Windows 10 License Terms](https://www.microsoft.com/content/dam/microsoft/usetm/documents/windows/10/oem-pre-installed/UseTerms_OEM_Windows_10_English.pdf).

As a workaround, you can perform instant recovery of multiple databases in parallel using the [Restore-VESQLIRDatabase](https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restore-vesqlirdatabase.html?ver=13) PowerShell cmdlet.

* If you plan to perform scheduled or manual switchover, make sure that the mount server volume with the write cache has enough free disk space to store the changes of the published database. By default, the write cache is stored in the C:\ProgramData\Veeam\Backup\IRCache\ folder of the mount server. For more information on how to configure the write cache folder, see [Specify Mount Server Settings](repository_mount_server.md).
* Instant recovery to a Microsoft SQL Server failover cluster requires 2 free drive letters on each cluster node to mount a volume from the backup. If the backed-up machine has multiple volumes, the number of free drive letters on each cluster node must be twice the number of volumes in the backup. For more information, see [How Instant Recovery Works](vesql_instant_hiw.md).


