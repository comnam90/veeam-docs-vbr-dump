---
title: "Account Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_permissions.html"
last_updated: "3/4/2026"
product_version: "13.0.1.2067"
---

# Account Permissions


The accounts used to deploy and administer backup infrastructure components must have the following permissions.

Backup Server Windows Account Permissions

The Windows account used to install Veeam Backup & Replication on the backup server must have the following permissions.

Backup Server Windows Account Permissions

| Account | Required Permission |
| Setup Account | The account used to install Veeam Backup & Replication and Veeam Plug-in for Scale Computing HyperCore must have the Local Administrator permissions on the backup server. |
| Veeam Backup & Replication User Account | The account used to run Veeam Backup & Replication services must be a LocalSystem account or must have the Local Administrator permissions on the backup server. |

Scale Computing HyperCore Cluster Permissions

The account that the backup server uses to access the Scale Computing HyperCore cluster must have the Admin role assigned or posses the following permissions: Backup, VM Create/Edit, VM Delete, VM Power Controls, Cluster Settings.

Performing Guest Processing

[This section applies only to Veeam Plug-in for Scale Computing HyperCore v3]

To allow Veeam Backup & Replication to create application-consistent backups of Windows- and Linux-based VMs, the accounts that will be used to perform [guest processing operations](guest_processing.md) (such as transaction log truncation and guest file indexing) must have the permissions listed in this section.

|  |
| --- |
| Note |
| The Veeam Backup & Replication console does not provide a possibility to restore application data from application-consistent backups — you can do this using Veeam Explorers only. To see the list of permissions that must be granted to accounts that will be used to perform the restore operations, see [Veeam Explorers User Guide](explorers_introduction.md). |

Performing Guest Processing

| Account | Required Permission |
| Microsoft SQL Server | To back up Microsoft SQL Server data, the user whose account you plan to use must have the following permissions:   * SQL Server instance-level role: public and dbcreator. * Database-level roles and roles for the model system database: db\_backupoperator, db\_denydatareader, public;   for the master system database — db\_backupoperator, db\_datareader, public;  for the msdb system database — db\_backupoperator, db\_datareader, public, db\_datawriter.   * Securables: view any definition, view server state, connect SQL.   Tip: If you do not want to assign the permissions gradually, use an account that has Local Administrator permissions on the target VM and system Administrator permissions (with the Sysadmin role) on the target Microsoft SQL Server. |
| Microsoft Active Directory | To back up Microsoft Active Directory data, the account must be a member of the built-in Administrators group. |
| Microsoft Exchange | The account used to back up Microsoft Exchange data must have the local Administrator permissions on the machine where Microsoft Exchange is installed. |
| Oracle | The account specified at the Guest Processing step must be configured in the following way:   * For a Windows-based VM, the account must be a member of both the Local Administrator group and the ORA\_DBA group (if OS authentication is used). In addition, if ASM is used, then such an account must be a member of the ORA\_ASMADMIN group (for Oracle 12 and higher). * For a Linux-based VM, the account must be a Linux user elevated to root. The account must have the home directory created.   To back up Oracle databases, you can specify the following options at the [Oracle](sch_backup_job_create_gp_oracle.md) tab:   * Oracle account with SYSDBA privileges.   You can use, for example, the SYS Oracle account or any other Oracle account that has been granted SYSDBA privileges.   * Account specified for guest processing. That is, the Use guest credentials option selected.   In this case, the account that was specified at the Guest Processing step must be a member of the ORA\_DBA group for a Windows-based VM and OSASM, OSDBA and OINSTALL groups for a Linux-based VM.  To perform guest processing for Oracle databases on Linux servers, make sure that the /tmp directory is mounted with the exec option. Otherwise, you will get an error with the permission denial. |
| Microsoft SharePoint | To back up a Microsoft SharePoint Server, the account must have the Farm Administrator role.  To back up Microsoft SQL databases of the Microsoft SharePoint Server, the account must have permissions required for Microsoft SQL Server backup operations. |
| PostgreSQL | The account specified at the Guest Processing step must be a Linux user elevated to root. The account must have the home directory created.  For the directory specified as the temporary location for archive logs, the following permissions must be granted:   * The user running the PostgreSQL instance must have read, write, and execute (rwx) permissions. * The user selected in the backup job settings must have read and execute (rx) permissions.   To back up PostgreSQL instances, the account must have the superuser privileges for the PostgreSQL instance. For more information, see [PostgreSQL documentation](https://www.postgresql.org/docs/current/database-roles.html).  Note: If you back up data using vSphere API, the account specified at the Guest Processing step must be a root Linux user. |


