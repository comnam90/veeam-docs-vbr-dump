---
title: "Stop-VBREntraIDTenantRestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrentraidtenantrestore.html"
last_updated: "1/9/2025"
product_version: "13.0.1.1071"
---

# Stop-VBREntraIDTenantRestore

In this article

Short Description

Stops a Microsoft Entra ID tenant restore session.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBREntraIDTenantRestore -Session <VBREntraIDTenantRestoreSession> [-Graceful]  [<CommonParameters>] |

Detailed Description

This cmdlet stops an Entra ID tenant restore session. Use this cmdlet when you do not plan to restore any tenant data.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the session launched to restore a tenant. The cmdlet will stop this session. | Accepts the VBREntraIDTenantRestoreSession object. To create this object, run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. | True | Named | False |
| Graceful | Defines that the cmdlet will stop the session gracefully. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Entra ID Tenant Restore Session

This example shows how to stop a tenant restore session.

|  |
| --- |
| $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $tenantRestoreSession = Start-VBREntraIDTenantRestore -Backup $backup  ...  Stop-VBREntraIDTenantRestore -Session $tenantRestoreSession -Graceful |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $tenantRestoreSession variable.
3. Run the Stop-VBREntraIDTenantRestoreSession cmdlet. Set the $tenantRestoreSession variable as the Session parameter value. Provide the Graceful parameter.

Related Commands

* [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)
* [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md)

Page updated 1/9/2025

Page content applies to build 13.0.1.1071
