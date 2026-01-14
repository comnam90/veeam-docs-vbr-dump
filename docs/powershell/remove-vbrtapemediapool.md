---
title: "Remove-VBRTapeMediaPool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrtapemediapool.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRTapeMediaPool

In this article

Short Description

Removes a media pool.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRTapeMediaPool -MediaPool <VBRTapeMediaPool[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected media pool from Veeam Backup & Replication.

|  |
| --- |
| ![Remove-VBRTapeMediaPool](images/icon_important.webp) Important! |
| Removing media pools has the following restrictions:   * You can only delete custom media pools; predefined media pools cannot be deleted. * You cannot delete a media pool that contains tapes. To be able to delete such a pool, first move tapes from this pool to other media pools. * You cannot delete media pools used by an existing backup/files to tape copy job. In case you definitely have to disable this pool, you should first modify the corresponding job to target another media pool. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| MediaPool | Specifies the array of media pools. The cmdlet will remove these media pools. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Media Pool [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the media pool named Winserver MediaPool.  |  | | --- | | Get-VBRTapeMediaPool -Name "Winserver MediaPool" | Remove-VBRTapeMediaPool |  Perform the following steps:   1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRTapeMediaPool cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Media Pool [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the media pool represented by the $pool variable.  |  | | --- | | $pool = Get-VBRTapeMediaPool -Name "Winserver MediaPool"  Remove-VBRTapeMediaPool -MediaPool $pool |  Perform the following steps:   1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $pool variable. 2. Run the Remove-VBRTapeMediaPool cmdlet. Set the $pool variable as the MediaPool parameter value. |

Related Commands

[Get-VBRTapeMediaPool](get-vbrtapemediapool.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
