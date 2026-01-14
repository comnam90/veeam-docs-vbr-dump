---
title: "Restore-VBREntraIDTenantItemAttributes"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/restore-vbrentraidtenantitemattributes.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# Restore-VBREntraIDTenantItemAttributes

In this article

Short Description

Restores properties of Microsoft Entra ID items.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restore-VBREntraIDTenantItemAttributes -Session <VBREntraIDTenantRestoreSession> [-CredentialsId <Guid>] -RestorePoint <VBREntraIDTenantRestorePoint> -Item <VBREntraIDTenantItem> -IncludedProperties <VBREntraIDTenantItemIncludedProperty[]> [-Reason <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet restores properties of Entra ID items.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore session started to recover items backed-up by a tenant backup job. | Accepts the VBREntraIDTenantRestoreSession object. To create this object, run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. | True | Named | False |
| RestorePoint | Specifies a restore point from which you want to restore Entra ID items. | Accepts the VBREntraIDTenantRestorePoint object. To get this object, run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. | True | Named | False |
| Item | Specifies the item whose properties you want to restore. | Accepts the VBREntraIDTenantItem object. To get this object, run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. | True | Named | False |
| IncludedProperties | Specifies an array of the properties that you want to restore. | Accepts the VBREntraIDTenantItemIncludedProperty[] object. To create this object, run the [New-VBREntraIDTenantItemIncludedProperty](new-vbrentraidtenantitemincludedproperty.md) cmdlet. | True | Named | False |
| CredentialsId | Used only if you requested login using the [Request-VBREntraIDLogin](request-vbrentraidlogin.md) cmdlet.  Specifies the ID of the login session. Set the parameter value to the value returned by the [Request-VBREntraIDLogin](request-vbrentraidlogin.md) cmdlet. | Guid | False | Named | False |
| Reason | Specifies the reason of the restore operation. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

Guid.

Examples

Restoring Manager Reference of User

This example shows how to restore the manager reference of a user.

|  |
| --- |
| $tenantRestoreSession = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $oldRP = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "a66808bc-780e-46f2-8538-63ace3c8f9be"  $item = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "Test Admin"  $compareInfo = Compare-VBREntraIDTenantItem -Session $tenantRestoreSession -Item $item -OldRestorePoint $oldRP  $managerReferenceObj = New-VBREntraIDTenantItemIncludedProperty -PropertyId $compareInfo.References.Values[0].ReferenceId -GroupId $compareInfo.References.ReferenceType[0]  $sessionId = Restore-VBREntraIDTenantItemAttributes -Session $tenantRestoreSession -RestorePoint $oldRP -Item $item -IncludedProperties $managerReferenceObj |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $tenantRestoreSession variable.
2. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
3. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $oldRP variable.
4. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter value. Save the result to the $item variable.
5. Run the [Compare-VBREntraIDTenantItem](compare-vbrentraidtenantitem.md) cmdlet. Specify the following settings:

* Set the $tenantRestoreSession variable as the Session parameter value.
* Set the $item variable as the Item parameter value.
* Set the $oldRP variable as the OldRestorePoint parameter value.

* Save the result to the $compareInfo variable.

1. Run the [New-VBREntraIDTenantItemIncludedProperty](new-vbrentraidtenantitemincludedproperty.md) cmdlet. Specify the following settings:

* Set the $compareInfo.References.Values[0].ReferenceId variable as the PropertyId parameter value.

The manager reference ID is the first in the received array of references.

* Set the $compareInfo.References.ReferenceType[0] variable as the GroupId parameter value.

The manager reference is the first in the received array of references.

* Save the result to the $managerReferenceObj variable.

1. Run the Restore-VBREntraIDTenantItemAttributes cmdlet. Specify the following settings:

* Set the $tenantRestoreSession variable as the Session parameter value.
* Set the $oldRP variable as the RestorePoint parameter value.
* Set the $item variable as the Item parameter value.
* Set the $managerReferenceObj variable as the IncludedProperties parameter value.

* Save the result to the $sessionId variable.

Related Commands

* [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md)
* [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)
* [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md)
* [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md)
* [Compare-VBREntraIDTenantItem](compare-vbrentraidtenantitem.md)
* [New-VBREntraIDTenantItemIncludedProperty](new-vbrentraidtenantitemincludedproperty.md)

Page updated 7/28/2025

Page content applies to build 13.0.1.1071
