---
title: "Export-VBREntraIDTenantItemToJson"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrentraidtenantitemtojson.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Export-VBREntraIDTenantItemToJson


Short Description

Exports Microsoft Entra ID tenant item properties and metadata in the JSON format.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VBREntraIDTenantItemToJson -ExportMapping <VBREntraIDTenantItemExportMapping[]> -Session <VBREntraIDTenantRestoreSession>  [<CommonParameters>] |

Detailed Description

This cmdlet exports properties and metadata of Microsoft Entra ID items (users, groups, roles, administrative units, applications, conditional access policies, intune policies, contacts and devices) from a backup and saves the exported data in the JSON format.

To specify a restore point for data export, use the [New-VBREntraIDTenantItemExportMapping](new-vbrentraidtenantitemexportmapping.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| ExportMapping | Specifies an object with a restore point that you want to use when exporting Microsoft Entra ID item data. | Accepts an array of VBREntraIDTenantItemExportMapping objects. To get this object, run the [New-VBREntraIDTenantItemExportMapping](new-vbrentraidtenantitemexportmapping.md) cmdlet. | True | Named | False |
| Session | Specifies the session launched to export Microsoft Entra ID item data. | Accepts the VBREntraIDTenantRestoreSession object. To get this object, run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns a JSON string.

|  |
| --- |
| Note |
| All the data is exported as a single string. If you plan to export multiple items, consider running the cmdlet several times. |

Examples

Exporting Entra ID Tenant Item Data

This example shows how to export properties and metadata of the Admin-12 user backed-up by the Tenant-backup-1 job.

|  |
| --- |
| $backup = Get-VBREntraIDTenantBackup -Name "Tenant-backup-1"  $rp = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "61448046-067f-4908-88ad-31e785477fc6"  $item = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "Admin-12"  $mapping = New-VBREntraIDTenantItemExportMapping -Item $item -RestorePoint $rp  $session = Start-VBREntraIDTenantRestore -Backup $backup  $json = Export-VBREntraIDTenantItemToJson -ExportMapping $mapping -Session $session |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $rp variable.
3. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter values. Save the result to the $item variable.
4. Run the [New-VBREntraIDTenantItemExportMapping](new-vbrentraidtenantitemexportmapping.md) cmdlet. Set the $item variable as the Item parameter value, and the $rp variable as the RestorePoint parameter value. Save the result to the $mapping variable.
5. Run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $session variable.
6. Run the Export-VBREntraIDTenantItemToJson cmdlet and do the following:

* Set the $mapping variable as the ExportMapping parameter value.
* Set the $session variable as the Session parameter value.

* Save the result to the $json variable.

Related Commands

[New-VBREntraIDTenantItemExportMapping](new-vbrentraidtenantitemexportmapping.md)

Page updated 2026-06-11

