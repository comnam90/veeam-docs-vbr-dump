---
title: "Get-VBRArchiveExtent"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrarchiveextent.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Get-VBRArchiveExtent


Short Description

Returns the archive extent.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRArchiveExtent -Repository <VBRScaleOutBackupRepository[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the archive extent of scale-out backup repositories. The archive extent is an archive object storage repository that is added to the scale-out backup repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an array of scale-out backup repositories. The cmdlet will return the archive extent added to this repository. | Accepts the [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md) object. To get this object, run the [Add-VBRScaleOutBackupRepository](add-vbrscaleoutbackuprepository.md) cmdlet. | True | Named | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRArchiveExtent](vbrarchiveextent.md)

Examples

Getting Archive Extent

This example shows how to get the archive extents added to the scale-out backup repositories.

|  |
| --- |
| $repository = Get-VBRBackupRepository -ScaleOut  Get-VBRArchiveExtent -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter. Save the result to the $repository variable.
2. Run the Get-VBRCArchiveExtent cmdlet. Set the $repository variable as the Repository parameter value.

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)


