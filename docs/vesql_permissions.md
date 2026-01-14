---
title: "Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_permissions.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Permissions

In this article

The following table lists the user account permissions necessary to launch Veeam Explorer for Microsoft SQL Server and recover Microsoft SQL Server data.

| Operation | Required Roles and Permissions |
| --- | --- |
| Veeam Explorer for Microsoft SQL Server launch | The account used to run Veeam Explorer for Microsoft SQL Server must meet the following requirements:   * The account must be a member of the local Administrators or Users group on the machine where Veeam Explorer for Microsoft SQL Server is running.  * The account must have one of the following roles on the backup server:  * The Veeam Backup Administrator or Veeam Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for Microsoft SQL Server restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore, Publish, Instant Recovery | The account must be a member of the local Administrators group and must be granted the sysadmin role on the target Microsoft SQL Server machine. To learn more about Microsoft SQL Server roles, see [this Microsoft article](https://learn.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles?view=sql-server-ver16).  The sysadmin role is required for connections with Microsoft SQL Server Virtual Device Interface (VDI) that Veeam Explorer for Microsoft SQL Server uses to perform recovery operations. For more information, see [this Microsoft article](https://support.microsoft.com/en-us/topic/sql-server-vdi-backup-and-restore-operations-require-sysadmin-privileges-4797c4bc-ed60-8f1b-7978-8ee1cc701eab). |
| Staging Microsoft SQL Server configuration | The account used to connect to the staging server must be granted the sysadmin role on the Microsoft SQL Server machine.  If you want to use a local Microsoft SQL Server as a staging server and Veeam Explorer for Microsoft SQL Server runs under an account that does not belong to the local Administrators group, you must specify the current account for connection to the staging server, or you will get an impersonation error.  For more information on how to configure and use the staging Microsoft SQL Server, see [Configuring Staging SQL Server](vesql_configure_staging.md). |
| Restore from SQL plug-in backups | To be able to connect to a Microsoft SQL Server instance, the account used for starting Microsoft SQL Server backup and restore processes must meet the following conditions:   * The account must be added to the following roles: public, sysadmin. * If the account is not a member of the Administrators group, you must enable the Create Global Objects security policy for the account. For detailed instructions on how to manage the Create Global Objects security policy, see [this Microsoft article](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/create-global-objects). |

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
