---
title: "Disable-VBRCatalystCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrcatalystcopyjob.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRCatalystCopyJob

In this article

Short Description

Disables backup copy jobs for HPE StoreOnce repositories.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRCatalystCopyJob -Job <VBRCatalystCopyJob[]> [-PassThru] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet disables backup copy jobs for HPE StoreOnce repositories.

Run the [Enable-VBRCatalystCopyJob](enable-vbrcatalystcopyjob.md) cmdlet to enable backup copy jobs for HPE StoreOnce repositories.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of backup copy jobs for HPE StoreOnce repositories. The cmdlet will disable these jobs. | Accepts the VBRCatalystCopyJob[] object. To get this object, run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCatalystCopyJob object that contains settings of backup copy jobs for HPE StoreOnce repositories.

Examples

Disabling Backup Copy Job for HPE StoreOnce Repository

This example shows how to disable the StoreOnce copy job backup copy job for an HPE StoreOnce repository.

|  |
| --- |
| $job = Get-VBRCatalystCopyJob -Name "StoreOnce copy job"  Disable-VBRCatalystCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Disable-VBRCatalystCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
