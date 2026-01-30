---
title: "Add-VBRDiscoveredComputerConfigurationPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrdiscoveredcomputerconfigurationpolicy.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Add-VBRDiscoveredComputerConfigurationPolicy


Short Description

Updates Veeam Agent settings on discovered computers using available configuration options.

|  |
| --- |
| Important |
| Make sure to test this cmdlet in the lab before you run it in the production environment. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Update Veeam Agent settings on individual computers using available configuration options.

|  |
| --- |
| Add-VBRDiscoveredComputerConfigurationPolicy -AgentType {Windows | Linux | Mac | Unix} -ConfigurationOption <VBRDiscoveredComputerConfigurationOption[]> -DiscoveredComputer <VBRDiscoveredComputer[]>  [<CommonParameters>] |

* Update Veeam Agent settings on computers in a protection group using available configuration options.

|  |
| --- |
| Add-VBRDiscoveredComputerConfigurationPolicy -AgentType {Windows | Linux | Mac | Unix} -ConfigurationOption <VBRDiscoveredComputerConfigurationOption[]> -ProtectionGroup <VBRProtectionGroup[]>  [<CommonParameters>] |

Detailed Description

This cmdlet updates Veeam Agent settings on individual computers or computers in protection groups using available configuration options. New settings are applied after the rescan operation.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| AgentType | Specifies the type of a Veeam Agent:   * Windows * Linux * Mac * Unix | VBRAgentType | True | Named | True |
| ConfigurationOption | Specifies the configuration option that you want to assign to discovered computers. | Accepts the [VBRDiscoveredComputerConfigurationOption](vbrdiscoveredcomputerconfigurationoption.md)[] object. To get this object, run the [New-VBRDiscoveredComputerConfigurationOption](new-vbrdiscoveredcomputerconfigurationoption.md) cmdlet. | True | Named | True |
| DiscoveredComputer | Specifies an array of discovered computers. The cmdlet will assign the configuration option to these computers. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md)[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByPropertyName) |
| ProtectionGroup | Specifies an array of protection groups to which you want to assign the configuration option. | Accepts the [VBRProtectionGroup](vbrprotectiongroup.md)[] object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDiscoveredComputerConfigurationPolicy](vbrdiscoveredcomputerconfigurationpolicy.md)

Examples

Updating Path to Temporary Folder Storing SQL Backup Logs on Windows Computers

This example shows how to update the SqlTempLogPath registry value on Windows computers.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Windows"  $computers = Get-VBRDiscoveredComputer -ProtectionGroup $group  $SQLLogpath = New-VBRDiscoveredComputerConfigurationOption -Name "SqlTempLogPath" -Value "D:\Temp"  $configuration\_policy = Add-VBRDiscoveredComputerConfigurationPolicy -DiscoveredComputer $computers -AgentType Windows -ConfigurationOption $SQLLogpath |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $computers variable.
3. Run the [New-VBRDiscoveredComputerConfigurationOption](new-vbrdiscoveredcomputerconfigurationoption.md) cmdlet. Specify the Name and the Value parameter values. Save the result to the $SQLLogpath variable.
4. Run the Add-VBRDiscoveredComputerConfigurationPolicy cmdlet. Specify the following settings:

* Set the $computers variable as the DiscoveredComputer parameter value.
* Specify the AgentType parameter value.
* Set the $SQLLogpath variable as the ConfigurationOption parameter value.

Save the result to the $configuration\_policy variable.

Related Commands

* [New-VBRDiscoveredComputerConfigurationOption](new-vbrdiscoveredcomputerconfigurationoption.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)


