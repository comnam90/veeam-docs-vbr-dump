---
title: "Request-VBREntraIDLogin"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/request-vbrentraidlogin.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Request-VBREntraIDLogin

In this article

Short Description

Requests login to Microsoft Entra ID using an account associated with the tenant whose data you are restoring.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Request-VBREntraIDLogin -Session <VBREntraIDTenantRestoreSession>  [<CommonParameters>] |

Detailed Description

This cmdlet requests login to Entra ID using an account associated with the tenant whose data you are restoring. The login is required if the application used for restore does not have enough permissions of the application type. The permissions must be the same as for using an existing application. For more information, see the [Permissions](https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_permissions.html?ver=13) section in the User Guide for Microsoft Entra ID. By default, the application used while adding a tenant is also used for restore.

The cmdlet will provide you the verification code. Paste this code to the <https://microsoft.com/devicelogin> page. Then specify a Microsoft Entra user account that is associated with the tenant selected for restore. The account must have the same permissions as for creating a new application. The permissions are listed in the [Permissions](https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_permissions.html?ver=13) section in the User Guide for Microsoft Entra ID.

Use this cmdlet right after the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session for which you want to request login to Microsoft Entra ID. | Accepts the VBREntraIDTenantRestoreSession object. To get this object, run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

Guid.

Examples

Requesting Login to Entra ID

This example shows how to request login to Entra ID.

|  |
| --- |
| $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $tenantRestoreSession = Start-VBREntraIDTenantRestore -Backup $backup  ...  $requestId = Request-VBREntraIDLogin -Session $tenantRestoreSession |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $tenantRestoreSession variable.
3. Run the Request-VBREntraIDLogin cmdlet. Set the $tenantRestoreSession variable as the Session parameter value. Save the result to the $requestId variable.

Related Commands

* [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)
* [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
