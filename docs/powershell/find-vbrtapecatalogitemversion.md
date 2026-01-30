---
title: "Find-VBRTapeCatalogItemVersion"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrtapecatalogitemversion.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Find-VBRTapeCatalogItemVersion


Short Description

Looks for backed up versions of a file or folder.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Find-VBRTapeCatalogItemVersion -CatalogItem <VBRTapeCatalogItem>  [<CommonParameters>] |

Detailed Description

This cmdlet looks for backed-up versions of a file or folder to be further used by the [Start-VBRTapeFileRestore](start-vbrtapefilerestore.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CatalogItem | Specifies a file or folder. The cmdlet will find versions of this file or folder. | Accepts the VBRTapeCatalogItem[] object. To get this object, run the [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRTapeCatalogItemVersion object that defines the versions of the tape catalog item (file, folder) with the following attributes: Id, CatalogItemId, BackupSetPointId, IsDeletedFromDisk, IsCorrupted, Location, Size, CreationTime, LastWriteTime, BackupSetWriteTime, IsDirectory.

Examples

Getting Version of File Backed-Up by Tape Job

This example shows how to get versions of a file backed-up by the tape job.

|  |
| --- |
| $item = Find-VBRTapeCatalogItem  Find-VBRTapeCatalogItemVersion -CatalogItem $item[3] |

Perform the following steps:

1. Run the [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) cmdlet. Save the result to the $item variable.
2. Run the Find-VBRTapeCatalogItemVersion cmdlet. Set the $item variable as the CatalogItem parameter value.

Related Commands

[Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md)


