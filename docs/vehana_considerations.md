---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vehana_considerations.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


This section lists considerations and known limitations of Veeam Explorer for SAP HANA.

General

* When Veeam Explorer for SAP HANA is installed on a server on which both Veeam Backup & Replication and Veeam Backup for Microsoft 365 are installed, the notification settings will be inherited from the Veeam Backup & Replication Global Notification settings.
* [For Linux-based backup servers] All open Explorer sessions become non-responsive after backup server switchover or failback. To continue browsing and restoring your data, you must reopen the sessions.

Restore

* Veeam Explorer for SAP HANA does not support restore using PowerShell Direct, VIX API or vSphere Automation API.
* Before you restore a tenant database, make sure that the system database on the target server is running.
* Veeam Explorer for SAP HANA does not support restore of the system database to another server.
* Veeam Explorer for SAP HANA does not support restore from backups created by Veeam Plug-In for SAP HANA on Linux machines running on IBM Power Systems.
* You cannot use Veeam Explorer for SAP HANA to restore your data if the OS user credentials in your SAP HANA backup policy are configured using an SSH private key — use the SSH credentials option instead.
* Before you restore an SAP HANA tenant database to another server, make sure SAP HANA is installed on the target server. For more information on supported SAP HANA support package stacks, see [System Requirements](vehana_systemreqs.md).

* Before you restore an SAP HANA tenant database, make sure that the target system has an SAP HANA SPS that is the same or newer than the one installed on the backed-up system.

* The target server to which you restore your data must have Veeam Plug-In for SAP HANA installed and configured, otherwise the restore operation will fail. To do this, add the machine to a protection group in Veeam Backup & Replication or install the plug-in manually.

* Before you restore an SAP HANA tenant database to another server, make sure that the account used to connect the plug-in on the target server to the backup server and backup repository meets the following requirements:

* The account must have either the Veeam Backup Administrator, or both the Veeam Backup Operator and Veeam Restore Operator roles. You can also use the account under which the backup was created. For more information on how to assign Veeam Backup & Replication roles, see [Managing Users and Roles](users_roles.md).
* The account must have access permissions to the backup repository where the backup resides. For more information, see [Access and Encryption Settings on Repositories](repository_permissions.md).

If the account does not meet these requirements, you must configure the plug-in on the target server with the credentials of an account that meets the requirements or with a recovery token. To do this, go to /opt/veeam/VeeamPluginforSAPHANA on the target server and run the following command:

|  |
| --- |
| hxeadm@saphana01:/opt/veeam/VeeamPluginforSAPHANA> SapBackintConfigTool --set-backup-for-restore |

For more information about this command, see [Restore to Another Server (System Copy)](restore_saphana_other_server.md).

* Before you restore a database, make sure that the target server has enough free disk space or the restore process will freeze.
* You cannot restore SAP HANA data from multiple backups in parallel to the same target machine.
* Before you restore a system database, make sure that automatic file rotation for the backup.log file is disabled or the restore process will freeze.
* If you restore a tenant database with a custom name to another server, make sure that the name does not contain keywords that belong to the RESERVED\_KEYWORDS system view. To get a list of these keywords, run the following query on your SAP HANA system:

|  |
| --- |
| SELECT \* FROM RESERVED\_KEYWORDS ORDER BY RESERVED\_KEYWORD |

* Veeam Explorer for SAP HANA can only restore from backups created with Veeam Backup & Replication 12.1 (build 12.1.0.2131) and later. This applies to both backups created in the console and with a standalone Veeam Plug-In for SAP HANA.
* Before restoring your SAP HANA data with PowerShell, make sure that the following conditions are met:

* The target system has a supported SAP HANA SPS.
* The target system has an SAP HANA SPS that is the same or newer than the one installed on the backed-up system.
* The backup repository contains at least one full backup.

* If you want to restore multiple databases, you cannot select system databases and tenant databases within the same restore operation. This is because you cannot simultaneously restore the system database of an SAP HANA system and its tenant databases — the system database is shut down during its restore process, while tenant databases require the system database to be online during theirs.
* If you disable a backup job managed by a standalone plug-in (where the backed-up machine has catalog\_backup\_using\_backint set to true in the global.ini file) or an application backup policy managed by Veeam Backup & Replication, the restore process will freeze. This is because after recovering the data, SAP HANA automatically creates a new backup catalog and sends it to the backint as part of the restore process, which requires the backup job or the application backup policy to be active.
* If you restore the system database to a state of an earlier point in time, all tenant databases created after that point of time will be deleted from the target server. You will need to restore those tenant databases within a separate restore operation.

* You cannot assign backup prefixes to backups created with application backup policies in Veeam Backup & Replication. To be able to assign backup prefixes to your backup, create a backup with a standalone Veeam Plug-In for SAP HANA. For more information, see [Database Protection](sap_hana_backup.md).
* Before you restore a tenant database using the SSL protocol, make sure that the target SAP HANA system is properly configured to use SSL and that the backup server has SAP Common Crypto Library installed. For more information about how to install SAP Common Crypto Library on Windows machines, see the [SAP Help Portal](https://help.sap.com/docs/SAP_DATA_SERVICES/e54136ab6a4a43e6a370265bf0a2d744/c049e28431ee4e8280cd6f5d1a8937d8.html?locale=en-US).
* [For Windows-based backup servers] If you are using secure restore, the backup server is running Microsoft Windows Server 2012 or 2016 and you are using SAP Common Crypto Library 8.5.51 or higher, you must export the SSL private key with the Triple DES encryption algorithm. SAP Common Crypto Library 8.5.51 or higher uses the AES 256 encryption algorithm as default for PKCS #12 encryption, while this encryption algorithm is not supported in Microsoft Windows Server 2012 and 2016.


