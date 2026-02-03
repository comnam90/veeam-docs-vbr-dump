---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_permissions.html"
last_updated: "1/9/2026"
product_version: "13.0.1.1071"
---

# Permissions


The accounts used to deploy and administer backup infrastructure components must have the following permissions.

Backup Server Windows Account

The account used to install Veeam Backup & Replication on a Windows-based machine must have the following permissions.

| Account | Required Permission |
| --- | --- |
| Setup Account | The account used to install Veeam Backup & Replication and Nutanix AHV Plug-in must have the Local Administrator permissions on the backup server. |
| Veeam Backup & Replication User Account | The account used to run Veeam Backup & Replication services must be a LocalSystem account or must have the Local Administrator permissions on the backup server. |

Nutanix AHV Cluster Administrator Account

The Nutanix AHV administrator account that Veeam Plug-in for Nutanix AHV uses to access the Prism Central or cluster must have privileges of the Cluster Admin or Prism Admin role. For more information on user access control, see [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Nutanix-Security-Guide-v7_3:ssp-ssp-role-based-access-control-pc-c.html).

Performing Guest Processing

To allow Veeam Backup & Replication to create application-consistent backups of Windows- and Linux-based VMs, the accounts that will be used to perform [guest processing operations](guest_processing.md) (such as transaction log truncation and guest file indexing) must have the permissions listed in this section.

|  |
| --- |
| Note |
| The Veeam Backup & Replication console does not provide a possibility to restore application data from application-consistent backups — you can do this using Veeam Explorers only. To see the list of permissions that must be granted to accounts that will be used to perform the restore operations, see the [Veeam Explorers User Guide](https://helpcenter.veeam.com/docs/vbr/explorers/explorers_introduction.html?ver=13). |

Backup Permissions for Windows-Based VMs

For Windows-based VMs, you must choose an account that has administrator privileges. Note that the Log on as a batch job permission must be granted to the account and the Deny log on as a batch job policy must not be defined. Other permissions depend on applications that you plan to back up:

| Application | Required Permission |
| --- | --- |
| Microsoft SQL Server | To back up Microsoft SQL Server data, the user whose account you plan to use must have the following permissions:   * SQL Server instance-level role: public and dbcreator. * Database-level roles and roles for the model system database: db\_backupoperator, db\_denydatareader, public; * Securables: view any definition, view server state, connect SQL.   Tip: If you do not want to assign the permissions gradually, use an account that has local Administrator permissions on the target VM and system Administrator permissions (with the Sysadmin role) on the target Microsoft SQL Server. |
| Microsoft Active Directory | The account used to back up Microsoft Active Directory data or a Domain Controller server must be a member of the built-in Administrators group.  The account used to back up a Read-Only Domain controller can have permissions of a delegated RODC administrator account. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc755310%28v%3Dws.10%29#Anchor_1). |
| Microsoft Exchange | The account used to back up Microsoft Exchange data must have the local Administrator permissions on the machine where Microsoft Exchange is installed. |
| Oracle | The account used to communicate with VM guest OSes must be a member of both the Local Administrator group and the ORA\_DBA group (if OS authentication is used). In addition, if ASM is used, then such an account must be a member of the ORA\_ASMADMIN group (for Oracle 12 and higher).  The account used to back up Oracle databases must have have the following permissions:   * Oracle account with SYSDBA privileges.   You can use, for example, the SYS Oracle account or any other Oracle account that has been granted SYSDBA privileges.   * Account specified for guest processing. That is, the Use guest credentials option selected.   In this case, the account that was specified at the Guest Processing step must be a member of the ORA\_DBA group. |
| Microsoft SharePoint | The account used to back up Microsoft SharePoint server data must have the Farm Administrator role.  The account used to back up Microsoft SQL databases of the Microsoft SharePoint Server must have the same privileges as that of [Microsoft SQL Server](#vesql). |

|  |
| --- |
| Tip |
| The account must be specified either in the DOMAIN\USERNAME (for Active Directory accounts) or in the HOST\USERNAME (for local user accounts) format. |

Backup Permissions for Linux-Based VMs

For Linux-based VMs, you must choose an account of a root user or a user elevated to root. Note that the account must have the /home directory created.Other permissions depend on applications that you plan to back up:

| Application | Required Permission |
| --- | --- |
| Oracle | The account used to back up Oracle databases must have have the following permissions:   * Oracle account with SYSDBA privileges.   You can use, for example, the SYS Oracle account or any other Oracle account that has been granted SYSDBA privileges.   * Account specified for guest processing. That is, the Use guest credentials option selected.   In this case, the account that was specified at the Guest Processing step must be a member of the OSASM, OSDBA and OINSTALL groups.  Note: To perform guest processing of Oracle databases running on Linux servers, make sure that the /tmp directory is mounted with the exec option. Otherwise, you will get a permission denial error. |
| PostgreSQL | The account used to back up PostgreSQL instances must have superuser privileges for the PostgreSQL instance. For more information, see [PostgreSQL documentation](https://www.postgresql.org/docs/current/database-roles.html).  The following permissions must be granted to access the folder used as a temporary location for archive logs:   * The user running the PostgreSQL instance must have read, write, and execute (rwx) permissions. * The user selected in the backup job settings to access the guest OS must have read and execute (rx) permissions. |


