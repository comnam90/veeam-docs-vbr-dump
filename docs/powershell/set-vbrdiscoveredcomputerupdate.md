---
title: "Set-VBRDiscoveredComputerUpdate"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrdiscoveredcomputerupdate.html"
last_updated: "1/3/2024"
product_version: "13.0.1.1071"
---

# Set-VBRDiscoveredComputerUpdate

In this article

Short Description

Assigns Veeam Agent private fixes to discovered computers.

Applies to

Product Edition: Community, Standard,  Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRDiscoveredComputerUpdate -Update <VBRDiscoveredComputerUpdate[]> [-DiscoveredComputer <VBRDiscoveredComputer[]>] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet assigns Veeam Agent private fixes to selected discovered computers. You can use this cmdlet to instruct Veeam Backup & Replication to send specified private fixes only to the associated discovered computers.

If you configured protection group deployment settings to automatically upgrade Veeam Agents, Veeam Backup & Replication will send private fixes from the distribution server to discovered computers and install them at the next scheduled discovery operation.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Update | Specifies the array of private fixes. The cmdlet will assign these private fixes to discovered computers.  Note: Every time you run the cmdlet, Veeam Backup & Replication re-assigns selected private fixes to a new set of discovered computers specified by the DiscoveredComputer parameter.  To unassign private fixes from discovered computers, run the cmdlet without the DiscoveredComputer parameter. | Accepts the [VBRDiscoveredComputerUpdate](vbrdiscoveredcomputerupdate.md)[] object. To get this object, run the [Get-VBRDiscoveredComputerUpdate](get-vbrdiscoveredcomputerupdate.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| DiscoveredComputer | Specifies the array of discovered computers. The cmdlet will assign private fixes to these computers. | Accepts the [VBRDiscoveredComputer[]](vbrdiscoveredcomputer.md) object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | False | Named | True (ByProperty Name) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDiscoveredComputerUpdate[]](vbrdiscoveredcomputerupdate.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Assigning Private Fix to Discovered Computers of Protection Group

|  |  |
| --- | --- |
| This example shows how to assign a private fix to discovered computers of a protection group.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "Support\_East"  $discovered = Get-VBRDiscoveredComputer -ProtectionGroup $group  $fix = Get-VBRDiscoveredComputerUpdate -Id "188235"  Set-VBRDiscoveredComputerUpdate -DiscoveredComputer $discovered -Update $fix -PassThru  Id                      : 188235  AgentType               : Windows  AgentVersion            : 2.1.10.304  OperatingSystemPlatform : Unknown  OperatingSystemVersion  :  Path                    : C:\Program Files\Veeam\Veeam Distribution Service\Fixes\VAW\kb.188235  AppliedTo               : {81a586bd-efc7-4280-8591-2bed0b43296f, 38d778f1-1906-44b0-871a-1db9097581a8}  Name                    : VAW.kb.188235.exe |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $discovered variable. 3. Run the [Get-VBRDiscoveredComputerUpdate](get-vbrdiscoveredcomputerupdate.md) cmdlet. Specify the Id parameter value. Save the result to the $fix variable. 4. Run the Set-VBRDiscoveredComputerUpdate cmdlet. Set the $discovered variable as the DiscoveredComputer parameter value. Set the $fix variable as the Update parameter value. Provide the PassThru parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Association Between Private Fix and Discovered Computers

|  |  |
| --- | --- |
| This example shows how to remove association between a private fix and discovered computers.  |  | | --- | | $fix = Get-VBRDiscoveredComputerUpdate -Id "188235"  Set-VBRDiscoveredComputerUpdate -Update $fix -PassThru  Id                      : 188235  AgentType               : Windows  AgentVersion            : 2.1.10.304  OperatingSystemPlatform : Unknown  OperatingSystemVersion  :  Path                    : C:\Program Files\Veeam\Veeam Distribution Service\Fixes\VAW\kb.188235  AppliedTo               : {}  Name                    : VAW.kb.188235.exe |  Perform the following steps:   1. Run the [Get-VBRDiscoveredComputerUpdate](get-vbrdiscoveredcomputerupdate.md) cmdlet. Specify the Id parameter value. Save the result to the $fix variable. 2. Run the Set-VBRDiscoveredComputerUpdate cmdlet. Set the $fix variable as the Update parameter value. Provide the PassThru parameter. |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)
* [Get-VBRDiscoveredComputerUpdate](get-vbrdiscoveredcomputerupdate.md)

Page updated 1/3/2024

Page content applies to build 13.0.1.1071
