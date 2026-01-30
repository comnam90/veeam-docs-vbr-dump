---
title: "New-VBRRecoveryMediaISOTarget"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrrecoverymediaisotarget.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# New-VBRRecoveryMediaISOTarget


Short Description

Creates the path for saving Veeam Recovery Media in the ISO file format.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create the user defined Veeam Recovery Media ISO file path.

|  |
| --- |
| New-VBRRecoveryMediaISOTarget -DiscoveredComputer <VBRDiscoveredComputer> [<CommonParameters>] |

* Create the default Veeam Recovery Media ISO file path.

|  |
| --- |
| New-VBRRecoveryMediaISOTarget -Path <String> [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRRecoveryMediaISOTarget object. This object contains the path to the ISO file. Use this object to create Veeam Recovery Media in the ISO file format with the [Add-VBRDiscoveredComputerRecoveryMedia](add-vbrdiscoveredcomputerrecoverymedia.md) cmdlet.

You can specify the full path to the ISO file or use the default one. The default ISO file path includes the path to the Documents folder and the ISO file name containing the name of the protected computer.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies the path for saving Veeam Recovery Media in the ISO file format. The cmdlet will create the object containing this file path. | String | False | Named | True (ByProperty Name) |
| DiscoveredComputer | Specifies a discovered computer. The cmdlet will create the object containing the default Veeam Recovery Media ISO file path for this computer. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md) object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRRecoveryMediaISOTarget object that contains the path to the ISO file.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating User Defined Veeam Recovery Media ISO File Path

|  |  |
| --- | --- |
| This command creates the user defined Veeam Recovery Media ISO file path.  |  | | --- | | New-VBRRecoveryMediaISOTarget -Path "c:\image.iso"  Path                                                                                             Type  ----                                                                                             ----  c:\image.iso                                                                                      ISO | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Default Veeam Recovery Media ISO File Path for Selected Computer

|  |  |
| --- | --- |
| This example shows how to create the default Veeam Recovery Media ISO file path for a selected computer.  |  | | --- | | $computer = Get-VBRDiscoveredComputer | Where {$\_.name -eq "support.east.local"}  New-VBRRecoveryMediaISOTarget -DiscoveredComputer $computer  Path                                                                                             Type  ----                                                                                             ----  C:\Users\Administrator\Documents\VeeamRecoveryMedia\_SUPPORT.EAST.LOCAL.iso                        ISO |  Perform the following steps:   1. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Use the Where-Object method to get the computer. Save the result to the $computer variable. 2. Run the New-VBRRecoveryMediaISOTarget cmdlet. Set the $computer variable as the DiscoveredComputer parameter value. |

Related Commands

* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)
* [Add-VBRDiscoveredComputerRecoveryMedia](add-vbrdiscoveredcomputerrecoverymedia.md)


