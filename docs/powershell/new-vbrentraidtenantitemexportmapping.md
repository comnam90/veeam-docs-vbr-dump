---
title: "New-VBREntraIDTenantItemExportMapping"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrentraidtenantitemexportmapping.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBREntraIDTenantItemExportMapping


Short Description

Defines an object with a restore point that you want to use when exporting Microsoft Entra ID item data.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBREntraIDTenantItemExportMapping -Item <VBREntraIDTenantItem> -RestorePoint <VBREntraIDTenantRestorePoint>  [<CommonParameters>] |

Detailed Description

This cmdlet defines an object that specifies a restore point for Microsoft Entra ID item data export performed by running the [Export-VBREntraIDTenantItemToJson](export-vbrentraidtenantitemtojson.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Item | Specifies the backed-up tenant item whose data you want to export. | Accepts the VBREntraIDTenantItem object. To get this object, run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. | True | Named | False |
| RestorePoint | Specifies a restore point from which you want to export the item data. | Accepts the VBREntraIDTenantRestorePoint object. To get this object, run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBREntraIDTenantItemExportMapping object that defines an object with a restore point that you want to use when exporting Microsoft Entra ID item data.

Examples

Defining Restore Point for Multiple Items

This example shows how to specify a restore point for 2 users whose data you plan to export.

|  |
| --- |
| $backup = Get-VBREntraIDTenantBackup -Name "Tenant-backup-1"  $rp = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "61448046-067f-4908-88ad-31e785477fc6"  $items = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "Admin-12","Admin-13"  $mapping = New-VBREntraIDTenantItemExportMapping -Item $items[2] -RestorePoint $rp |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $rp variable.
3. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter values. Save the result to the $items variable.
4. Run the [New-VBREntraIDTenantItemExportMapping](new-vbrentraidtenantitemexportmapping.md) cmdlet. Set the $items variable as the Item parameter value, and the $rp variable as the RestorePoint parameter value. Save the result to the $mapping variable.

Related Commands

[Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md)

[Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md)

Page updated 2026-06-15

