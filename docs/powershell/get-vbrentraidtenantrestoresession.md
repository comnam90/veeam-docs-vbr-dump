---
title: "Get-VBREntraIDTenantRestoreSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrentraidtenantrestoresession.html"
last_updated: "1/14/2025"
product_version: "13.0.1.1071"
---

# Get-VBREntraIDTenantRestoreSession

In this article

Short Description

Returns restore sessions started to recover Microsoft Entra ID tenant backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBREntraIDTenantRestoreSession [-Id <Guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore sessions started to recover Entra ID tenant backups. If you do not provide any parameters, the cmdlet returns all restore sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of restore session IDs. The cmdlet will return restore sessions with these IDs. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the array of [VBREntraIDTenantRestoreSession](vbrentraidtenantrestoresession.md) objects that contain settings of restore sessions started to recover Entra ID tenant backups.

Examples

Getting Entra ID Tenant Restore Session by ID

This example shows how to get a tenant restore session by its ID.

|  |
| --- |
| $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $tenantRestoreSession = Start-VBREntraIDTenantRestore -Backup $backup  ...  $session = Get-VBREntraIDTenantRestoreSession -Id $tenantRestoreSession.Id |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $tenantRestoreSession variable.
3. Run the Get-VBREntraIDTenantRestoreSession cmdlet. Set the $tenantRestoreSession.Id variable as the Id parameter value. Save the result to the $session variable.

Related Commands

* [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)
* [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md)

Page updated 1/14/2025

Page content applies to build 13.0.1.1071
