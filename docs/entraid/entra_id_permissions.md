---
title: "Permissions"
product: "vbr"
doc_type: "entraid"
source_url: "https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_permissions.html"
last_updated: "12/17/2025"
product_version: "13.0.1.1071"
---

# Permissions


The accounts that Veeam Backup for Microsoft Entra ID uses to deploy and manage backup infrastructure components must be granted the following permissions.

Veeam Backup & Replication User Account Permissions

A user account that you plan to use when installing and working with Veeam Backup & Replication must have permissions described in the Veeam Backup & Replication User Guide, section [Installing and Using Veeam Backup & Replication](https://helpcenter.veeam.com/docs/vbr/userguide/required_permissions.html?ver=13#rpvbr).

Microsoft Entra Roles and Permissions

Veeam Backup for Microsoft Entra ID requires a Microsoft Entra application whose permissions are used to add Microsoft Entra ID tenants to the backup infrastructure and to perform backup and restore operations with Microsoft Entra ID resources.

Adding and Backing Up Tenants

You can [specify an existing application or instruct Veeam Backup & Replication to create a new one](entra_id_tenant_connection.md). The list of permissions granted to the Microsoft Entra application and the list of roles assigned to the Microsoft Entra ID user account that you use to create the application depend on the actions you plan to perform using the application.

| Application | Permissions |
| --- | --- |
| New | The Microsoft Entra ID user account associated with the tenant where the Microsoft Entra ID application will be created must have the following built-in roles assigned:   * [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) * [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator)   As an alternative, you can assign the [Global Administrator Microsoft Entra](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) built-in role. |
| Existing | To perform backup, the application must have the following permissions:   * [Microsoft Graph application permissions](https://learn.microsoft.com/en-us/graph/permissions-reference): AuditLog.Read.All, Directory.Read.All, Group.Read.All, MailboxSettings.Read, RoleManagement.Read.Directory, User.Read.All, Policy.Read.All, Policy.ReadWrite.ConditionalAccess, Agreement.Read.All, DeviceManagementConfiguration.Read.All. |
| To be able to further perform restore, the application must have the following permissions:   * [Microsoft Graph delegated permissions](https://learn.microsoft.com/en-us/graph/permissions-reference): Directory.ReadWrite.All, RoleManagement.ReadWrite.Directory, AdministrativeUnit.ReadWrite.All, Directory.AccessAsUser.All, Application.ReadWrite.All, Group.ReadWrite.All, Policy.ReadWrite.ConditionalAccess, Agreement.Read.All, DeviceManagementConfiguration.ReadWrite.All * [API delegated permissions](https://learn.microsoft.com/en-us/information-protection/develop/concept-api-permissions): user\_impersonation   Note: Make sure that the Allow public client flows option is enabled for the application. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/healthcare-apis/register-application#authentication-setting-confidential-vs-public). |

|  |
| --- |
| Important |
| By default, Veeam Backup for Microsoft Entra ID does not back up relationships between protected resources and management groups. If you want to add these relationships into the backup scope, you must perform additional configuration steps described in [this Veeam KB article.](https://www.veeam.com/kb4683) |

Restoring Tenant Data

To restore tenant data, Veeam Backup for Microsoft Entra ID uses the Microsoft Entra application that was used to [add the tenant](#add). This application has delegated access and acts on behalf of a user that you specify in the restore wizard.

This user must have with the following roles:

* [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
* [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator)
* [Exchange Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#exchange-administrator)
* [Groups Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#groups-administrator)
* [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator)
* [Privileged Authentication Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-authentication-administrator)
* [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator)
* [Intune Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)

As an alternative, you can use [Global Administrator Microsoft Entra](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) plus [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator) (recommended) or plus [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator) roles.


