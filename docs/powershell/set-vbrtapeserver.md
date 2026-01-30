---
title: "Set-VBRTapeServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrtapeserver.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Set-VBRTapeServer


Short Description

Modifies tape servers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRTapeServer -TapeServer <VBRTapeServer> [-Description <string>] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies tape server that was created before.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| TapeServer | Specifies the tape server you want to modify. | Accepts the [VBRTapeServer](vbrtapeserver.md) object. To get this object, run the [Get-VBRTapeServer](get-vbrtapeserver.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Description | Specifies the new description you want to apply to the tape server. | String | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeServer](vbrtapeserver.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Description of Tape Server [Using Variable]

|  |  |
| --- | --- |
| This example shows how to modify the description of the Sydney\_Tape\_Server tape server.  |  | | --- | | $tapeserver = Get-VBRTapeServer -Name "Sydney\_Tape\_Server"  Set-VBRTapeServer -TapeServer $tapeserver -Description "Sydney\_Remote\_Tape\_Server" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $tapeserver variable. 2. Run the Set-VBRTapeServer cmdlet. Set the $tapeserver variable as the TapeServer parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Description of Tape Server [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to modify the description of the Sydney\_Tape\_Server tape server.  |  | | --- | | Get-VBRTapeServer -Name "Sydney\_Tape\_Server" | Set-VBRTapeServer -Description "Sydney\_Remote\_Tape\_Server" -PassThru |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRTapeServer cmdlet. Specify the Description parameter value. Provide the PassThru parameter. |

Related Commands

[Get-VBRTapeServer](get-vbrtapeserver.md)


