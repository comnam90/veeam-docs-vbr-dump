---
title: "Compare-VBREntraIDTenantItem"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/compare-vbrentraidtenantitem.html"
last_updated: "1/9/2025"
product_version: "13.0.1.1071"
---

# Compare-VBREntraIDTenantItem

In this article

Short Description

Compares backed-up objects between two restore points or a restore point and the production state.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Compare-VBREntraIDTenantItem -Session <VBREntraIDTenantRestoreSession> -Item <VBREntraIDTenantItem> -OldRestorePoint <VBREntraIDTenantRestorePoint> [-NewRestorePoint <VBREntraIDTenantRestorePoint>] [-ShowUnchangedAttributes]  [<CommonParameters>] |

Detailed Description

This cmdlet compares backed-up objects between two restore points or a restore point and the production state.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore session started to recover items backed-up by a tenant backup job. | Accepts the VBREntraIDTenantRestoreSession object. To create this object, run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. | True | Named | False |
| Item | Specifies the backed-up object that you want to compare. | Accepts the VBREntraIDTenantItem object. To get this object, run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. | True | Named | False |
| OldRestorePoint | Specifies a restore point. The cmdlet will use this restore point as the starting point for the comparison. | Accepts the VBREntraIDTenantRestorePoint object. To get this object, run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. | True | Named | False |
| NewRestorePoint | Specifies a restore point. The cmdlet will use this restore point as the second point for the comparison.  Note: If you do not specify this parameter, the cmdlet will compare the restore point specified in OldRestorePoint with the production state of the backed-up object. | Accepts the VBREntraIDTenantRestorePoint object. To get this object, run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. | False | Named | False |
| ShowUnchangedAttributes | Defines that the cmdlet will show unchanged properties of the backed-up object.  Default: False. | SwichParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDTenantItemComparisonResult](vbrentraidtenantitemcomparisonresult.md) object that contains compare state of backed-up objects.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Comparing User Attributes Between Two Restore Points

|  |  |
| --- | --- |
| This example shows how to compare user attributes between two restore points.  |  | | --- | | $tenantRestoreSession = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $newRP = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "61448046-067f-4908-88ad-31e785477fc6"  $oldRP = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "a66808bc-780e-46f2-8538-63ace3c8f9be"  $item = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "Test Admin"  $compareInfo = Compare-VBREntraIDTenantItem -Session $tenantRestoreSession -Item $item -OldRestorePoint $oldRP -NewRestorePoint $newRP |  Perform the following steps:   1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $tenantRestoreSession variable. 2. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 3. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $newRP variable. 4. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $oldRP variable. 5. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter value. Save the result to the $item variable. 6. Run the Compare-VBREntraIDTenantItem cmdlet. Specify the following settings:  * Set the $tenantRestoreSession variable as the Session parameter value. * Set the $item variable as the Item parameter value. * Set the $oldRP variable as the OldRestorePoint parameter value. * Set the $newRP variable as the NewRestorePoint parameter value.  * Save the result to the $compareInfo variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Comparing User Attributes Between Restore Point and Production

|  |  |
| --- | --- |
| This example shows how to compare user attributes between a restore point and the production state.  |  | | --- | | $tenantRestoreSession = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $oldRP = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "a66808bc-780e-46f2-8538-63ace3c8f9be"  $item = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "Test Admin"  $compareInfo = Compare-VBREntraIDTenantItem -Session $tenantRestoreSession -Item $item -OldRestorePoint $oldRP |  Perform the following steps:   1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $tenantRestoreSession variable. 2. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 3. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $oldRP variable. 4. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter value. Save the result to the $item variable. 5. Run the Compare-VBREntraIDTenantItem cmdlet. Specify the following settings:  * Set the $tenantRestoreSession variable as the Session parameter value. * Set the $item variable as the Item parameter value. * Set the $oldRP variable as the OldRestorePoint parameter value.  * Save the result to the $compareInfo variable. |

Related Commands

* [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md)
* [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)
* [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md)
* [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md)

Page updated 1/9/2025

Page content applies to build 13.0.1.1071
