---
title: "Guest Processing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/permissions_guest_processing.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Guest Processing


To use guest OS processing (application-aware processing, pre-freeze and post-thaw scripts, transaction log processing, guest file indexing and file exclusions), make sure to configure your accounts according to the requirements listed in this section. For more information on guest processing, see [Guest Processing](guest_processing.md).

All user accounts used for guest processing of Windows VMs must have the following permissions:

* Logon as a batch job granted
* Deny logon as a batch job not set

Group Managed Service Accounts (gMSAs) must also have the following permissions:

* Logon as a service granted.
* Deny logon as a service not set.

Other permissions depend on applications that you back up. You can find the permissions for backup operations in the following table. For restore operation permissions, see Permissions sections in the [Veeam Explorers User Guide](https://helpcenter.veeam.com/docs/vbr/explorers/explorers_introduction.html?ver=13).

Guest Processing

| Application | Required Permission |
| Microsoft SQL Server | To back up Microsoft SQL Server data, the user whose account you plan to use must be:   * Local Administrator on the target VM. * System administrator (has the Sysadmin role) on the target Microsoft SQL Server.   If you need to provide minimal permissions, the account must be assigned the following roles and permissions:   * SQL Server instance-level role: public and dbcreator. * Database-level roles and roles for the model system database: db\_backupoperator, db\_denydatareader, public; for the master system database — db\_backupoperator, db\_datareader, public;  for the msdb system database — db\_backupoperator, db\_datareader, public, db\_datawriter. * Securables: view any definition, view server state, connect SQL. |
| Microsoft Active Directory | To back up Microsoft Active Directory data, the account must be a member of the built-in Administrators group. |
| Microsoft Exchange | To back up Microsoft Exchange data, the account must have the local Administrator permissions on the machine where Microsoft Exchange is installed. |
| Oracle | The account specified at the Guest Processing step must be configured in the following way:   * For a Windows-based VM, the account must be a member of both the Local Administrator group and the ORA\_DBA group (if OS authentication is used). In addition, if ASM is used, then such an account must be a member of the ORA\_ASMADMIN group (for Oracle 12 and higher). * For a Linux-based VM, the account must be a Linux user elevated to root. The account must have the home directory created.   To back up Oracle databases, you can specify the following options on the [Oracle](backup_job_vss_oracle_vm.md) tab:   * Oracle account with SYSDBA privileges.   You can use the SYS Oracle account or any other Oracle account that has been granted SYSDBA privileges.   * Account specified for guest processing. That is, the Use guest credentials option selected.   In this case, the account that was specified at the Guest Processing step must be a member of the ORA\_DBA group for a Windows-based VM and OSASM, OSDBA and OINSTALL groups for a Linux-based VM.  To perform guest processing for Oracle databases on Linux servers, make sure that the /tmp directory is mounted with the exec option. Otherwise, you will get a permission denial error. |
| Microsoft SharePoint | To back up a Microsoft SharePoint Server, the account must have the Farm Administrator role.  To back up the Microsoft SQL databases of the Microsoft SharePoint Server, the account must have the permissions required for [Microsoft SQL Server](#vesql) backup operations. |
| PostgreSQL | The account specified at the Guest Processing step must be a Linux user elevated to root. The account must have the home directory created.  The directory specified as the temporary location for archive logs must have the following permissions:   * The user running the PostgreSQL instance must have read, write, and execute (rwx) permissions. * The user selected in the backup job settings must have read and execute (rx) permissions.   For more information, see [PostgreSQL WAL Files Settings](backup_job_vss_postgresql_vm.md) for VMware vSphere or [PostgreSQL WAL Files Settings](backup_job_vss_postgresql_hv.md) for Microsoft Hyper-V.  To back up PostgreSQL instances, the account must have the superuser privileges on the PostgreSQL instance. For more information, see [PostgreSQL documentation](https://www.postgresql.org/docs/current/database-roles.html).  Note: If you back up data using vSphere API, the account specified at the Guest Processing step must be a root Linux user. |

Consider the following general requirements when choosing a user account:

* [For guest OS file indexing] For Windows-based workloads, choose an account that has administrative permissions. For Linux-based workloads, choose an account of a root user or user elevated to root.

* To use networkless guest processing over vSphere Web Services (vSphere) or PowerShell Direct (Hyper-V), you must specify one of the following accounts at the Guest Processing step of the backup wizard. Check that the account also has the permissions listed in the table.

* If Windows User Account Control (UAC) is enabled, specify Local Administrator (MACHINE\Administrator) or Domain Administrator (DOMAIN\Administrator) account.
* If UAC is disabled, specify an account that is a member of the built-in Administrators group.
* [For vSphere] For Linux-based VMs, specify a root account.

* [If you plan to use guest processing over network for workloads without listed applications] For Windows-based workloads, choose an account that has administrative permissions. For Linux-based workloads, choose an account of a root user or user elevated to root.
* When using Active Directory accounts, provide an account in the DOMAIN\Username format.
* When using local user accounts, provide an account in the Username or HOST\Username format.
* To process a Domain Controller server, use an account that is a member of the DOMAIN\Administrators group.
* To back up a Read-Only Domain controller, a delegated RODC administrator account is sufficient. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc755310%28v%3Dws.10%29#Anchor_1).

Page updated 2026-07-29

