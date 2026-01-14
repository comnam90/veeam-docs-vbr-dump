---
title: "Erase-VBRTapeMedium"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/erase-vbrtapemedium.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Erase-VBRTapeMedium

In this article

Short Description

Erases data from tape.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Erase-VBRTapeMedium -Medium <VBRTapeMedium[]> [-Long] [-Wait] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet erases data from the selected tapes. The erased tapes are moved to the Free media pool.

The cmdlet provides two scenarios for erasing options:

* Short: only the tape data header is cleared. The tape becomes available for overwriting. Short erase is a quick procedure.
* Long: all data is cleared from tape. This procedure requires more time.

|  |
| --- |
| Important |
| You cannot erase data from the following types of tapes:   * Offline tapes * Tapes used by any jobs * Tapes with software or hardware protection |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies the array of tapes. The cmdlet will erase these tapes. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object, GUID or string. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Long | Defines that the cmdlet will perform the long (full) erase.  Default: short erase. | SwitchParameter | False | Named | False |
| Wait | Defines that the command waits for the erase process(es) to complete before accepting more input. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupSession](vbrbackupsession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Running Short Erase on Selected Tape

|  |  |
| --- | --- |
| This example shows how to run short erase on the 00170010 tape.  |  | | --- | | $tape = Get-VBRTapeMedium -Name "00170010"  Erase-VBRTapeMedium -Medium $tape |  Perform the following steps:   1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable. 2. Run the Erase-VBRTapeMedium cmdlet. Set the $tape variable as the Medium parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Running Long Erase on Selected Tape

|  |  |
| --- | --- |
| This example shows how to run long erase on the 00170010 tape.  |  | | --- | | $tape = Get-VBRTapeMedium -Name "00170010"  Erase-VBRTapeMedium -Medium $tape -Long |  Perform the following steps:   1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable. 2. Run the Erase-VBRTapeMedium cmdlet. Set the $tape variable as the Medium parameter value. Provide the Long parameter. |

Related Commands

[Get-VBRTapeMedium](get-vbrtapemedium.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
