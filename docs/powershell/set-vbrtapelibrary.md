---
title: "Set-VBRTapeLibrary"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrtapelibrary.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Set-VBRTapeLibrary

In this article

Short Description

Modifies a tape library.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRTapeLibrary -TapeLibrary <VBRTapeLibrary> -Name <string> [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the name of the selected tape library.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| TapeLibrary | Specifies the tape library you want to modify. | Accepts the [VBRTapeLibrary](vbrtapelibrary.md) object. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the new name you want to assign to the library. | String | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeLibrary](vbrtapelibrary.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Tape Library Name [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to modify the name of the tape library named HP MSL G3 Series 3.00 to New York Remote Tape.  |  | | --- | | Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00" | Set-VBRTapeLibrary -Name "New York Remote Tape" -PassThru  Drives       : {Tape0, Tape1} Enabled      : True Model        : MSL G3 Series Slots        : 24 TapeServerId : 00000000-0000-0000-0000-000000000000 Type         : Automated State        : Online Id           : 2f1fdc3c-8a97-4fa0-b631-74a039e64d5c Name         : New York Remote Tape Description  : New York office Tape Library |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRTapeLibrary cmdlet. Specify the Name parameter value. Provide the PassThru parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Tape Library Name [Using Variable]

|  |  |
| --- | --- |
| This example shows how to modify the name of the US Remote Tape tape library.  |  | | --- | | $tapelibrary = Get-VBRTapeLibrary -Name "US Remote Tape"  Set-VBRTapeLibrary -TapeLibrary $tapelibrary -Name "New York Remote Tape" |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. Save the result to the $tapelibrary variable. 2. Run the Set-VBRTapeLibrary cmdlet. Set the $tapelibrary variable as the TapeLibrary parameter values. Specify the Name parameter value. |

Related Commands

[Get-VBRTapeLibrary](get-vbrtapelibrary.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
