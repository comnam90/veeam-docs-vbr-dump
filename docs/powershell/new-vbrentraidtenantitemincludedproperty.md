---
title: "New-VBREntraIDTenantItemIncludedProperty"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrentraidtenantitemincludedproperty.html"
last_updated: "1/9/2025"
product_version: "13.0.1.1071"
---

# New-VBREntraIDTenantItemIncludedProperty

In this article

Short Description

Defines an object with item properties or references that you want to restore.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBREntraIDTenantItemIncludedProperty -PropertyId <String> [-GroupId <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines an object with item properties or references that you want to restore.

To get the item properties and references that you can restore, use the [Compare-VBREntraIDTenantItem](compare-vbrentraidtenantitem.md) cmdlet. This cmdlet can also help you define if a field is a property or reference.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| PropertyId | Specifies different values depending on what you plan to restore:   * [For property restore] Specifies a property name. A property can be a surname, city and others. * [For reference restore] Specifies a reference ID. A reference can be a manager, group membership and others. | String | True | Named | False |
| GroupId | Used for reference restore.  Specifies a reference type. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDTenantItemIncludedProperty](vbrentraidtenantitemincludedproperty.md) object that defines properties that you want to restore further.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Object with Property

|  |  |
| --- | --- |
| This example shows how to define an object that contains a property that you further want to restore.  |  | | --- | | $tenantRestoreSession = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $oldRP = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "a66808bc-780e-46f2-8538-63ace3c8f9be"  $item = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "Test Admin"  $compareInfo = Compare-VBREntraIDTenantItem -Session $tenantRestoreSession -Item $item -OldRestorePoint $oldRP  $cityPropertyObj = New-VBREntraIDTenantItemIncludedProperty -PropertyId $compareInfo.Properties.PropertyName[0] |  Perform the following steps:   1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $tenantRestoreSession variable. 2. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 3. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $oldRP variable. 4. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter value. Save the result to the $item variable. 5. Run the [Compare-VBREntraIDTenantItem](compare-vbrentraidtenantitem.md) cmdlet. Specify the following settings:  * Set the $tenantRestoreSession variable as the Session parameter value. * Set the $item variable as the Item parameter value. * Set the $oldRP variable as the OldRestorePoint parameter value.  * Save the result to the $compareInfo variable.  1. Run the New-VBREntraIDTenantItemIncludedProperty cmdlet. Specify the following settings:  * Set the $compareInfo.Properties.PropertyName[0] variable as the PropertyId parameter value.   The city property is the first in the received array of properties.   * Save the result to the $cityPropertyObj variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Object with Reference

|  |  |
| --- | --- |
| This example shows how to define an object that contains a reference that you further want to restore.  |  | | --- | | $tenantRestoreSession = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $oldRP = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "a66808bc-780e-46f2-8538-63ace3c8f9be"  $item = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "Test Admin"  $compareInfo = Compare-VBREntraIDTenantItem -Session $tenantRestoreSession -Item $item -OldRestorePoint $oldRP  $managerReferenceObj = New-VBREntraIDTenantItemIncludedProperty -PropertyId $compareInfo.References.Values[0].ReferenceId -GroupId $compareInfo.References.ReferenceType[0] |  Perform the following steps:   1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $tenantRestoreSession variable. 2. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 3. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $oldRP variable. 4. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter value. Save the result to the $item variable. 5. Run the [Compare-VBREntraIDTenantItem](compare-vbrentraidtenantitem.md) cmdlet. Specify the following settings:  * Set the $tenantRestoreSession variable as the Session parameter value. * Set the $item variable as the Item parameter value. * Set the $oldRP variable as the OldRestorePoint parameter value.  * Save the result to the $compareInfo variable.  1. Run the New-VBREntraIDTenantItemIncludedProperty cmdlet. Specify the following settings:  * Set the $compareInfo.References.Values[0].ReferenceId variable as the PropertyId parameter value.   The manager reference ID is the first in the received array of references.   * Set the $compareInfo.References.ReferenceType[0] variable as the GroupId parameter value.   The manager reference is the first in the received array of references.   * Save the result to the $managerReferenceObj variable. |

Related Commands

* [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md)
* [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)
* [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md)
* [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md)
* [Compare-VBREntraIDTenantItem](compare-vbrentraidtenantitem.md)

Page updated 1/9/2025

Page content applies to build 13.0.1.1071
