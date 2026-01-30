---
title: "Disable-VBRTapeDrive"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrtapedrive.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRTapeDrive


Short Description

Disables a selected tape library drive.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRTapeDrive -Drive <VBRTapeDrive[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet disables a selected tape library recording drive. When you disable a drive, Veeam Backup & Replication stops using it for read or write operations. You can disable a drive, for example, for Maintenance.

Run the [Enable-VBRTapeDrive](enable-vbrtapedrive.md) cmdlet to enable the drive.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Drive | Specifies the array of drives. The cmdlet will disable these drives. | Accepts the [VBRTapeDrive[]](vbrtapedrive.md) object. To get this object, run the [Get-VBRTapeDrive](get-vbrtapedrive.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling Drive of Selected Library [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to disable one drive of the HP MSL G3 Series 3.00 library.  |  | | --- | | Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00" | Get-VBRTapeDrive | Select -Last 1 | Disable-VBRTapeDrive |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the [Get-VBRTapeDrive](get-vbrtapedrive.md) cmdlet. Select the last drive in the list. Pipe this all to Disable-VBRTapeDrive. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Drive of Selected Library [Using Variable]

|  |  |
| --- | --- |
| This example shows how to disable a first drive in HP MSL G3 Series 3.00 tape library.  |  | | --- | | $library = Get-VBRTapeLibrary -Name "HP MSL G3 Series 3.00"  $drive =  Get-VBRTapeDrive -Library $library | Select -First 1  Disable-VBRTapeDrive -Drive $drive |  Perform the following steps:   1. Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. Specify the Name parameter value. Save the result to the $library variable. 2. Run the [Get-VBRTapeDrive](get-vbrtapedrive.md) cmdlet. Set the $library variable as the Library parameter value. Select the first drive. Save the result to the $drive variable. 3. Run the Disable-VBRTapeDrive cmdlet. Set the $drive variable as the Drive parameter value. |

Related Commands

[Get-VBRTapeDrive](get-vbrtapedrive.md)


