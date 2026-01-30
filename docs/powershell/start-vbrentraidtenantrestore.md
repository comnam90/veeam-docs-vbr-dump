---
title: "Start-VBREntraIDTenantRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrentraidtenantrestore.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Start-VBREntraIDTenantRestore


Short Description

Starts a restore session for a Microsoft Entra ID tenant.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBREntraIDTenantRestore -Backup <VBREntraIDTenantBackup>  [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session for an Entra ID tenant.

If the application used for adding the tenant does not have the required roles, use the [Request-VBREntraIDLogin](request-vbrentraidlogin.md) cmdlet to get access to Entra ID. For more information on the required permissions, see the [Permissions](https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_permissions.html?ver=13) section in the User Guide for Microsoft Entra ID.

Then you can use the following cmdlets:

* [Restore-VBREntraIDTenantItem](restore-vbrentraidtenantitem.md) to restore the entire Entra ID items (users, roles and so on).
* [Restore-VBREntraIDTenantItemAttributes](restore-vbrentraidtenantitemattributes.md) to restore Entra ID item attributes.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies a tenant backup from which you want to restore data. | Accepts the VBREntraIDTenantBackup object. To get this object, run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. | True | 0 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDTenantRestoreSession](vbrentraidtenantrestoresession.md) object that contains properties of the tenant restore session.

Examples

Starting Entra ID Tenant Restore Session

This example shows how to start a tenant restore session for the backup created by the Tenant backup job.

|  |
| --- |
| $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $tenantRestoreSession = Start-VBREntraIDTenantRestore -Backup $backup |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the Start-VBREntraIDTenantRestore cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $tenantRestoreSession variable.

Related Commands

[Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)


