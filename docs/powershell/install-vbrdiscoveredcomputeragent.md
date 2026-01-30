---
title: "Install-VBRDiscoveredComputerAgent"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/install-vbrdiscoveredcomputeragent.html"
last_updated: "5/15/2024"
product_version: "13.0.1.1071"
---

# Install-VBRDiscoveredComputerAgent


Short Description

Installs Veeam Agents on discovered computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Install-VBRDiscoveredComputerAgent -DiscoveredComputer <VBRDiscoveredComputer[]> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet installs Veeam Agents on discovered computers.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| DiscoveredComputer | Specifies the array of discovered computers. The cmdlet will install Veeam Agents on these computers. | Accepts the [VBRDiscoveredComputer[]](vbrdiscoveredcomputer.md) object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Installing Veeam Agents on Discovered Computers of Selected Protection Group

|  |  |
| --- | --- |
| This example shows how to install Veeam Agents on discovered computers of a selected protection group.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "East Support"  $computers = Get-VBRDiscoveredComputer -ProtectionGroup $group  Install-VBRDiscoveredComputerAgent -DiscoveredComputer $computers |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $computers variable. 3. Run the Install-VBRDiscoveredComputerAgent cmdlet. Set the $computers variable as the DiscoveredComputer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Protection Group and Installing Veeam Agents on Discovered Computers of This Group

|  |  |
| --- | --- |
| This example shows how to create a protection group, manually discover computers of this group and install Veeam Agents on discovered computers of this group.  |  | | --- | | $computers = @("172.19.51.53", "sup-v8931") | ForEach { New-VBRIndividualComputerCustomCredentials -HostName $\_ -Credentials "support\jsmith" }  $compscope = New-VBRIndividualComputerContainer -CustomCredentials $computers  $group = Add-VBRProtectionGroup -Name "Support\_East" -Container $compscope  Rescan-VBREntity -Entity $group -Wait  $discovered = Get-VBRDiscoveredComputer -ProtectionGroup $group  Install-VBRDiscoveredComputerAgent -DiscoveredComputer $discovered |  Perform the following steps:   1. Create a scope of computers for a protection group:  * Run the [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md) cmdlet. Use the ForEach statement to apply the same credentials to multiple computers. Save the result to the $computers variable. * Run the [New-VBRIndividualComputerContainer](new-vbrindividualcomputercontainer.md) cmdlet. Set the $computers variable as the CustomCredentialsContainer parameter value. Save the result to the $compscope variable.  1. Run the [Add-VBRProtectionGroup](add-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Set the $compscope variable as the Container parameter value. Save the result to the $group variable. 2. Run the [Rescan-VBREntity](rescan-vbrentity.md) cmdlet. Set the $group variable as the Entity parameter value. Provide the Wait parameter. 3. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $discovered variable. 4. Run the Install-VBRDiscoveredComputerAgent cmdlet. Set the $discovered variable as the DiscoveredComputer parameter value. |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Rescan-VBREntity](rescan-vbrentity.md)
* [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md)
* [New-VBRIndividualComputerContainer](new-vbrindividualcomputercontainer.md)
* [Add-VBRProtectionGroup](add-vbrprotectiongroup.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)


