---
title: "Enable-VBRArchiveExtentSealedMode"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrarchiveextentsealedmode.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRArchiveExtentSealedMode


Short Description

Enables the Sealed mode for the archive extent.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRArchiveExtentSealedMode -ArchiveExtent <VBRArchiveExtent[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet enables the Sealed mode for the archive extent of the scale-out backup repository.

Run the [Disable-VBRArchiveExtentSealedMode](disable-vbrarchiveextentsealedmode.md) cmdlet to disable the Sealed mode.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ArchiveExtent | Specifies the archive extent. The cmdlet will set this extent to the Sealed mode. | Accepts the [VBRArchiveExtent](vbrarchiveextent.md) object. To get this object, run the [Get-VBRArchiveExtent](get-vbrarchiveextent.md) cmdlet. | True | Named | True (ByValue, |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Enabling Sealed Mode for Archive Extent

This example shows how to enable Sealed mode for the specified capacity extent of the scale-out backup repository.

|  |
| --- |
| $repository = Get-VBRBackupRepository -ScaleOut  $extent = Get-VBRArchiveExtent -Repository $repository  Enable-VBRArchiveExtentSealedMode -ArchiveExtent $extent |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter. Save the result to the $repository variable.
2. Run the [Get-VBRArchiveExtent](get-vbrarchiveextent.md) cmdlet. Set the $repository variable as the Repository parameter value. Save the result to the $extent variable.
3. Run the Enable-VBRArchiveExtentSealedMode cmdlet. Set the $extent variable as the ArchiveExtent parameter value.

Related Commands

* [Get-VBRArchiveExtent](get-vbrarchiveextent.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


