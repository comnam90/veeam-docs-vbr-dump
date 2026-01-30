---
title: "Get-VBREntraIDTenantRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrentraidtenantrestorepoint.html"
last_updated: "1/9/2025"
product_version: "13.0.1.1071"
---

# Get-VBREntraIDTenantRestorePoint


Short Description

Returns restore points of a Microsoft Entra ID tenant backup.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBREntraIDTenantRestorePoint [-Id <Guid[]>] -Backup <VBREntraIDTenantBackup>  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points of an Entra ID tenant backup.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the ID of the restore point that you want to get. | Guid[] | False | Named | False |
| Backup | Specifies a tenant backup whose restore points you want to get. | Accepts the VBREntraIDTenantBackup object. To get this object, run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the array of [VBREntraIDTenantRestorePoint](vbrentraidtenantrestorepoint.md) objects that contain properties of restore points.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Restore Points

|  |  |
| --- | --- |
| This example shows how to get all restore points of the backup created by the Tenant backup job.  |  | | --- | | $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $restorePoints = Get-VBREntraIDTenantRestorePoint -Backup $backup |  Perform the following steps:   1. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBREntraIDTenantRestorePoint cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorePoints variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Point by ID

|  |  |
| --- | --- |
| This example shows how to get a restore point by its ID.  |  | | --- | | $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $restorePoint = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "d24a05e0-4caa-46ef-b046-d9bb5a9dbd9c" |  Perform the following steps:   1. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBREntraIDTenantRestorePoint cmdlet. Specify the following settings:  * Set the $backup variable as the Backup parameter value. * Specify the Id parameter value. * Save the result to the $restorePoint variable. |

Related Commands

[Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)


