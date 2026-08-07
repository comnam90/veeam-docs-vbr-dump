---
title: "Account Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Account Permissions


To perform backup and restore operations, accounts that the plug-in uses to perform data protection and disaster recovery operations must be granted the following permissions.

Veeam Backup & Replication User Account Permissions

A user account that you plan to use when installing and working with Veeam Backup & Replication must have permissions described in section [Installing and Using Veeam Backup & Replication](required_permissions.md).

HPE Morpheus VM Essentials User Permissions

Veeam Plug-in for HPE Morpheus VM Essentials requires a user account in the HPE Morpheus VM Essentials infrastructure where data protection and disaster recovery tasks will be performed. To allow Veeam Plug-in for HPE Morpheus VM Essentials to access the HPE Morpheus VM Essentials manager and resources that you want to protect, the account used by Veeam Plug-in for HPE Morpheus VM Essentials must have a specific set of permissions:

* Admin > Appliance Settings
* Admin > Environment Settings
* Admin > Provisioning Settings
* Admin > Service Plans
* API > Execution Request
* Backups > Backups
* Infrastructure > Clouds
* Infrastructure > Clusters
* Infrastructure > Compute
* Infrastructure > Groups
* Infrastructure > Keypairs
* Infrastructure > Manage Placement
* Infrastructure > Networks
* Infrastructure > Storage
* Library > Virtual Images
* Lifecycle > Power Control
* Lifecycle > Reconfigure
* Operations > Wiki
* Provisioning > Administrator
* Provisioning > Instances: Add
* Provisioning > Instances: Delete
* Provisioning > Instances: Edit
* Provisioning > Instances: List
* Snapshots > Snapshots

For more information on access permissions, see [HPE Morpheus VM Essentials documentation](https://support.hpe.com/hpesc/public/docDisplay?docId=sd00006775en_us&page=GUID-BB3046E2-F2D4-4B45-8B85-E4982E255B2F.html).

Performing Guest Processing

To allow Veeam Backup & Replication to create application-consistent backups of Windows- and Linux-based VMs, the accounts that will be used to perform [guest processing operations](guest_processing.md) (such as transaction log truncation and guest file indexing) must have the permissions listed in this section.

|  |
| --- |
| Note |
| The Veeam Backup & Replication console does not provide a possibility to restore application data from application-consistent backups — you can do this using Veeam Explorers only. To see the list of permissions that must be granted to accounts that will be used to perform the restore operations, see the [Veeam Explorers User Guide](https://helpcenter.veeam.com/docs/vbr/explorers/explorers_introduction.html?ver=13). |

Backup Permissions for Windows-Based VMs

For Windows-based VMs, you must choose an account that has administrator privileges. Note that the Log on as a batch job permission must be granted to the account and the Deny log on as a batch job policy must not be defined. Other permissions depend on applications that you plan to back up:

Backup Permissions for Windows-Based VMs

| Application | Required Permission |
| Microsoft SQL Server | To back up Microsoft SQL Server data, the user whose account you plan to use must have the following permissions:   * SQL Server instance-level role: public and dbcreator. * Database-level roles and roles for the model system database: db\_backupoperator, db\_denydatareader, public; for the master system database — db\_backupoperator, db\_datareader, public;  for the msdb system database — db\_backupoperator, db\_datareader, public, db\_datawriter. * Securables: view any definition, view server state, connect SQL.   Tip: If you do not want to assign the permissions gradually, use an account that has local Administrator permissions on the target VM and system Administrator permissions (with the Sysadmin role) on the target Microsoft SQL Server. |
| Microsoft Active Directory | The account used to back up Microsoft Active Directory data or a Domain Controller server must be a member of the built-in Administrators group.  The account used to back up a Read-Only Domain controller can have permissions of a delegated RODC administrator account. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc755310%28v%3Dws.10%29#Anchor_1). |
| Microsoft Exchange | The account used to back up Microsoft Exchange data must have the local Administrator permissions on the machine where Microsoft Exchange is installed. |
| Oracle | The account used to communicate with VM guest OSes must be a member of both the Local Administrator group and the ORA\_DBA group (if OS authentication is used). In addition, if ASM is used, then such an account must be a member of the ORA\_ASMADMIN group (for Oracle 12 and higher).  The account used to back up Oracle databases must have the following permissions:   * Oracle account with SYSDBA privileges.   You can use, for example, the SYS Oracle account or any other Oracle account that has been granted SYSDBA privileges.   * Account specified for guest processing. That is, the Use guest credentials option selected.   In this case, the account that was specified at the Guest Processing step must be a member of the ORA\_DBA group. |
| Microsoft SharePoint | The account used to back up Microsoft SharePoint server data must have the Farm Administrator role.  The account used to back up Microsoft SQL databases of the Microsoft SharePoint Server must have the same privileges as that of [Microsoft SQL Server](#vesql). |

|  |
| --- |
| Tip |
| The account must be specified either in the DOMAIN\USERNAME (for Active Directory accounts) or in the HOST\USERNAME (for local user accounts) format. |

Backup Permissions for Linux-Based VMs

For Linux-based VMs, you must choose an account of a root user or a user elevated to root. Note that the account must have the /home directory created. Other permissions depend on applications that you plan to back up:

Backup Permissions for Linux-Based VMs

| Application | Required Permission |
| Oracle | The account used to back up Oracle databases must have the following permissions:   * Oracle account with SYSDBA privileges.   You can use, for example, the SYS Oracle account or any other Oracle account that has been granted SYSDBA privileges.   * Account specified for guest processing. That is, the Use guest credentials option selected.   In this case, the account that was specified at the Guest Processing step must be a member of the OSASM, OSDBA and OINSTALL groups.  Note: To perform guest processing of Oracle databases running on Linux servers, make sure that the /tmp directory is mounted with the exec option. Otherwise, you will get a permission denial error. |
| PostgreSQL | The account used to back up PostgreSQL instances must have superuser privileges for the PostgreSQL instance. For more information, see [PostgreSQL documentation](https://www.postgresql.org/docs/current/database-roles.html).  The following permissions must be granted to access the folder used as a temporary location for archive logs:   * The user running the PostgreSQL instance must have read, write, and execute (rwx) permissions. * The user selected in the backup job settings to access the guest OS must have read and execute (rx) permissions. |

Page updated 2026-07-22

