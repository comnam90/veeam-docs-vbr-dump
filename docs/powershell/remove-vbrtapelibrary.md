---
title: "Remove-VBRTapeLibrary"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrtapelibrary.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRTapeLibrary


Short Description

Removes a specified tape library from Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRTapeLibrary -Library <VBRTapeLibrary[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a specified tape library from Veeam Backup & Replication.

When you remove a tape library, you stop managing it with your Veeam Backup & Replication console.

|  |
| --- |
| Important |
| Before you remove a tape library, consider the following limitations:   * Only the libraries in the offline status can be removed. To remove a tape library, you need to physically disconnect it from the tape server first. Alternatively, you can remove the tape server to which the tape library is connected. * You can remove the tape devices that are not used by any tape jobs. If any jobs are using the media pools assigned to the tape device, first redirect these jobs to other media pools. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Library | Specifies the array of tape libraries. The cmdlet will remove these tape libraries. | Accepts the [VBRTapeLibrary](vbrtapelibrary.md) object. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Tape Library [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove a tape library named HP MSL G3 Series 3.00.  |  | | --- | | Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00" | Remove-VBRTapeLibrary |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRTapeLibrary cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Tape Library [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove a tape library named HP MSL G3 Series 3.00.  |  | | --- | | $SydneyTapeLibrary = Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00"  Remove-VBRTapeLibrary -Library $SydneyTapeLibrary |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. 2. Run the Remove-VBRTapeLibrary cmdlet. Set the $SydneyTapeLibrary variable as the Library parameter values. |

Related Commands

[Get-VBRTapeLibrary](get-vbrtapelibrary.md)


