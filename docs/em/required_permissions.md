---
title: "required_permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/required_permissions.html"
last_updated: "10/29/2025"
product_version: "13.0.1.1071"
---


In this article

This section provides information on the account permissions required for installing, upgrading and using Veeam Backup Enterprise Manager on Microsoft Windows machines.

Veeam Backup Enterprise Manager

| Account | Required Permissions |
| --- | --- |
| Setup accounts | The account used to run the setup must have the local Administrator permissions on the target machine. |
| [Configuration database on PostgreSQL] The PostgreSQL account must be a superuser. |
| [Configuration database on Microsoft SQL Server] Your account must have the following Microsoft SQL Server permissions:   * To create a new Veeam Backup Enterprise Manager database during the setup process, the account must have the CREATE ANY DATABASE permission on the Microsoft SQL Server level. After the database is created, this account automatically gets the db\_owner role and can perform all operations with the database. If a database is created in advance (by a database administrator or Microsoft SQL Server administrator), the setup account must have the db\_owner role for the database. * To upgrade an existing Microsoft SQL Server database, the account must have the db\_owner role. |
| Veeam Backup Enterprise Manager service account | Use the Local System account as the [Veeam Backup Enterprise Manager Service](em_setup_specify_service_account.md) account. If you set another account to run this service, this account must have the following permissions:   * Local Administrator permissions on the Veeam Backup Enterprise Manager server. * Log on as a service permission (granted automatically to the [Veeam Backup Enterprise Manager Service](em_setup_specify_service_account.md) account).  * [Configuration database on PostgreSQL] The PostgreSQL account must be a superuser.  * [Configuration database on Microsoft SQL Server] Db\_datareader and db\_datawriter roles, as well as permissions to execute stored procedures for the Enterprise Manager configuration database. Alternatively, you can assign this account the db\_owner role for the this database to the service account. * Full Control NTFS permissions for the VBRCatalog or another folder where index files are stored.   To add Active Directory user or group accounts to the Veeam Backup Enterprise Manager roles, the Veeam Backup Enterprise Manager service must be started under the Active Directory service account that has permissions to enumerate Active Directory domains. Active Directory users have enough permissions to enumerate Active Directory domains by default. If you use the local machine account instead, you will get the "Cannot find user account DOMAIN\username" error. |
| Enterprise Manager user | To work with the Veeam Backup Enterprise Manager web UI, users must be assigned the Portal Administrator, Portal User, or Restore Operator role. For more information, see [Configuring Accounts and Roles](veeam_backup_em_roles.md). |
| vSphere Client Plug-in for Veeam Backup & Replication (optional) | The account used to install the plug-in and the vCenter Server account must belong to the same Active Directory domain in case of cross-domain access.  The account used to install the plug-in must be assigned the following vCenter Server permissions:   * To install the plug-in: Extension > Register extension * To uninstall the plug-in: Extension > Unregister extension |
| vSphere Self-Service Backup Portal user | The account used to work with vSphere Self-Service Backup Portal must have interactive logon permissions on the Enterprise Manager server. |

Page updated 10/29/2025

Page content applies to build 13.0.1.1071
