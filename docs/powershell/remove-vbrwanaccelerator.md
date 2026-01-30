---
title: "Remove-VBRWANAccelerator"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrwanaccelerator.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRWANAccelerator


Short Description

Removes a WAN accelerator.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRWANAccelerator -Accelerator <CWanAccelerator>  [<CommonParameters>] |

Detailed Description

This cmdlet removes the selected WAN accelerator.

When you remove a WAN accelerator, Veeam Backup & Replication unassigns the accelerator role from the server, so it is no longer used as a WAN accelerator. The actual server remains connected to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Accelerator | Specifies the WAN accelerator you want to remove. | Accepts the CWanAccelerator object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Selected WAN Accelerator [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the WAN Accelerator named WANAccelerator 1.  |  | | --- | | Get-VBRWANAccelerator -Name "WANAccelerator 1" | Remove-VBRWANAccelerator |  Perform the following steps:   1. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRWANAccelerator cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Selected WAN Accelerator [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the WAN Accelerator named WANAccelerator 1.  |  | | --- | | $a = Get-VBRWANAccelerator -Name "WANAccelerator 1"  Remove-VBRWANAccelerator -Accelerator $a |  Perform the following steps:   1. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save the result to the $a variable. 2. Run the Remove-VBRWANAccelerator cmdlet. Set the $a variable as the Accelerator parameter value. |

Related Commands

[Get-VBRWANAccelerator](get-vbrwanaccelerator.md)


