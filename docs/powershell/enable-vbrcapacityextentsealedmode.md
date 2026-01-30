---
title: "Enable-VBRCapacityExtentSealedMode"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcapacityextentsealedmode.html"
last_updated: "2/2/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRCapacityExtentSealedMode


Short Description

Enables Sealed mode for capacity extents.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRCapacityExtentSealedMode -CapacityExtent <VBRCapacityExtent[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet enables Sealed mode for capacity extents.

Run the [Disable-VBRCapacityExtentSealedMode](disable-vbrcapacityextentsealedmode.md) cmdlet to disable the Sealed mode for capacity extent of the scale-out backup repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CapacityExtent | Specifies a capacity extent of scale-out backup repositories. The cmdlet will enable Sealed mode for the specified capacity extent. | Accepts the [VBRCapacityExtent](vbrcapacityextent.md)[] object. To get this object, run the [Get-VBRCapacityExtent](get-vbrcapacityextent.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Enabling Sealed Mode for Capacity Extent

This example shows how to enable Sealed mode for the specified capacity extent of the scale-out backup repository.

|  |
| --- |
| $repository = Get-VBRBackupRepository -ScaleOut  $extent = Get-VBRCapacityExtent  Enable-VBRCapacityExtentSealedMode -CapacityExtent $extent |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter. Save the result to the $repository variable.
2. Run the [Get-VBRCapacityExtent](get-vbrcapacityextent.md) cmdlet. Save the result to the $extent variable.
3. Run the Enable-VBRCapacityExtentSealedMode cmdlet. Set the $extent variable as the CapacityExtent parameter value.

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRCapacityExtent](get-vbrcapacityextent.md)


