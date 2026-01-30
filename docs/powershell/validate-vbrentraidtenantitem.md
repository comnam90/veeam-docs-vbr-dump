---
title: "Validate-VBREntraIDTenantItem"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/validate-vbrentraidtenantitem.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Validate-VBREntraIDTenantItem


Short Description

Validates that a restore point contains data for the specified Microsoft Entra ID items.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Validate-VBREntraIDTenantItem -Session <VBREntraIDTenantRestoreSession> -RestorePointId <Guid> -Items <VBREntraIDTenantItem[]>  [<CommonParameters>] |

Detailed Description

This cmdlet checks that a restore point contains data for the specified Microsoft Entra ID items. Use this cmdlet before the [Restore-VBREntraIDTenantItem](restore-vbrentraidtenantitem.md) and [Restore-VBREntraIDTenantItemAttributes](restore-vbrentraidtenantitemattributes.md) cmdlets.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore session started to recover tenant data. | Accepts the VBREntraIDTenantRestoreSession object. To create this object, run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. | True | Named | False |
| RestorePointId | Specifies the ID of the restore point which you want to validate. | Guid | True | Named | False |
| Items | Specifies an array of tenant items. The cmdlet will check if data for these items is present in the specified restore point. | Accepts the VBREntraIDTenantItem[] object. To get this object, run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns None if the item data exists in the restore point. The cmdlet returns the array of [VBREntraIDTenantItem](vbrentraidtenantitem.md) objects if the item data does not exist in the restore point. This array contains items whose data is not present in the restore point.

Examples

Validating That Restore Point Contains Data

This example shows how to validate if a restore point contains information for the admin user.

|  |
| --- |
| $session = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $restorePoint = Get-VBREntraIDTenantRestorePoint -Backup $backup  $item = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "admin"  Validate-VBREntraIDTenantItem -Session $session -Items $item -RestorePointId $restorePoint[0].Id |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $session variable.
2. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorePoint variable.
3. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter values. Save the result to the $item variable.
4. Run the Validate-VBREntraIDTenantItem cmdlet. Specify the following settings:

* Set the $session variable as the Session parameter value.

* Set the $item variable as the Items parameter value.
* Set the $restorePoint[0].Id variable as the RestorePointId parameter value. $restorePoint[0].Id contains the ID of the first restore point.

Related Commands

* [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md)
* [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md)
* [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md)


