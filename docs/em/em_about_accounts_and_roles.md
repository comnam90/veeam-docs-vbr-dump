---
title: "em_about_accounts_and_roles"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_about_accounts_and_roles.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---


In this article

Accounts

Administrators can add accounts to Veeam Backup Enterprise Manager to grant users access to the website. Enterprise Manager offers the following account types: User, Group, External User and External Group.

| Type | Description | How to Sign In | Name Format |
| --- | --- | --- | --- |
| User | Local or AD user | By specifying a user name and password | * Windows-based Enterprise Manager: DOMAIN\Username (domain is optional) * Linux-based Enterprise Manager: Username@DOMAIN (domain is mandatory for AD users) |
| Group | Local or AD group | By specifying a user name and password | * Windows-based Enterprise Manager: DOMAIN\Groupname (domain is optional) * Linux-based Enterprise Manager: Groupname@DOMAIN (domain is mandatory for AD groups) |
| External User | IdP user | By using single sign-on\* | Username@Suffix |
| External Group | IdP group | By using single sign-on\* | Free-form string |
| vSphere Role | VMware vCenter Server role used to access the [Remote vSphere Client plug-in](remote_vsphere_client_plugin.md) | — | — |

\* For more information on the single sign-on capability, see [SAML Authentication Support](em_saml.md).

Roles

To provide an account with permissions, administrators assign one of the following roles to the account: Portal Administrator, Portal User or Restore Operator.

| Role | How Is Assigned | Access to Configuration | Permissions |
| --- | --- | --- | --- |
| Portal Administrator | * Initially by default to the users listed in the local Administrators group and the user who installed Enterprise Manager * By Portal Administrator in Configuration > Roles | Yes | Full access to all available operations on all tabs of the web UI |
| Portal User | By Portal Administrator in Configuration > Roles | No | * Access objects from the restore scope on the Machines and Files tabs * Run Quick Backup for machines from the restore scope on the Machines tab * Perform restore operations as permitted by the delegation settings * View information about all backup servers and jobs on the Dashboard, Reports, Jobs and Policies tabs |
| Restore Operator | By Portal Administrator in Configuration > Roles | No | * Access objects from the restore scope on the Machines and Files tabs * Perform restore operations as permitted by the delegation settings |

Users with the Portal User or Restore Operator role can access their restore scope — a list of objects that can be recovered by appropriate personnel. For example, the restore scope of database administrators is database servers (Microsoft SQL Server, Oracle or other), the restore scope of Exchange administrators is Exchange server machines, and so on. For more information on configuring restore scope, see [Configuring Restore Scope](veeam_backup_em_restore_scope.md).

|  |
| --- |
| Important |
| You can customize the restore scope if you have the Enterprise Plus edition of Veeam Backup & Replication. In other editions, this list includes all objects and cannot be customized. However, you can delegate recovery of entire machines, guest files, or selected file types. For more information, see [Configuring Permissions for File and Application Item Restore](configuring_restrictions_for_restore.md). |

Page updated 10/30/2025

Page content applies to build 13.0.1.1071
