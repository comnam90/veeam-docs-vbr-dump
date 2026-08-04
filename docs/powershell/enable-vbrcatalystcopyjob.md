---
title: "Enable-VBRCatalystCopyJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcatalystcopyjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Enable-VBRCatalystCopyJob (obsolete)


Short Description

Enables backup copy jobs for HPE StoreOnce repositories.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Enable-VBRStorageCopyJob](enable-vbrstoragecopyjob.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRCatalystCopyJob -Job <VBRCatalystCopyJob[]> [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet enables backup copy jobs for HPE StoreOnce repositories.

Run the [Disable-VBRCatalystCopyJob](disable-vbrcatalystcopyjob.md) cmdlet to disable backup copy jobs for HPE StoreOnce repositories.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Job | Specifies an array of backup copy jobs for HPE StoreOnce repositories. The cmdlet will enable these jobs. | Accepts the VBRCatalystCopyJob[] object. To get this object, run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCatalystCopyJob object that contains settings of backup copy jobs for HPE StoreOnce repositories.

Examples

Enabling Backup Copy Job for HPE StoreOnce Repository

This example shows how to enable the StoreOnce copy job backup copy job for an HPE StoreOnce repository.

|  |
| --- |
| $job = Get-VBRCatalystCopyJob -Name "StoreOnce copy job"  Enable-VBRCatalystCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Enable-VBRCatalystCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md)

Page updated 2026-06-12

