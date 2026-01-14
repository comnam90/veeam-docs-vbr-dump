---
title: "Get-VBREntraIDTenantItem"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrentraidtenantitem.html"
last_updated: "3/21/2025"
product_version: "13.0.1.1071"
---

# Get-VBREntraIDTenantItem

In this article

Short Description

Returns Microsoft Entra ID items that a backup contains.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBREntraIDTenantItem -Backup <VBREntraIDTenantBackup> -Type <VBREntraIDTenantItemType> [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Entra ID items that a backup contains.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the backup from which you want to get Entra ID items. | Accepts the VBREntraIDTenantBackup object. To get this object, run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. | True | Named | False |
| Type | Specifies the type of items that you want to return.  Note: Conditional Access policies are available only in Enterprise Plus and Veeam Universal License. | [VBREntraIDTenantItemType](enums.md#VBREntraIDTenantItemType) | True | Named | False |
| Name | Specifies an array of item display names. The cmdlet will return items with these display names.  Note: This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the array of [VBREntraIDTenantItem](vbrentraidtenantitem.md) objects that define settings of Entra ID items.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Groups by Name

|  |  |
| --- | --- |
| This example shows how to get backed-up groups whose displayed name start with "grp".  |  | | --- | | $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $groups = Get-VBREntraIDTenantItem -Backup $backup -Type Group -Name "grp\*" |  Perform the following steps:   1. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBREntraIDTenantItem cmdlet. Specify the following settings:  * Set the $backup variable as the Backup parameter value. * Specify the Type and Name parameter values. * Save the result to the $groups variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Administrative Units

|  |  |
| --- | --- |
| This example shows how to get backed-up administrative units.  |  | | --- | | $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $units = Get-VBREntraIDTenantItem -Backup $backup -Type AdminUnit |  Perform the following steps:   1. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBREntraIDTenantItem cmdlet. Specify the following settings:  * Set the $backup variable as the Backup parameter value. * Specify the Type parameter value. * Save the result to the $units variable. |

Related Commands

[Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)

Page updated 3/21/2025

Page content applies to build 13.0.1.1071
