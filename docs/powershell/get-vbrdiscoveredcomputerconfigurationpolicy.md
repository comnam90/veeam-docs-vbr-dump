---
title: "Get-VBRDiscoveredComputerConfigurationPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdiscoveredcomputerconfigurationpolicy.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Get-VBRDiscoveredComputerConfigurationPolicy


Short Description

Returns configuration options applied to protected computers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get the list of configuration options applied to individual computers.

|  |
| --- |
| Get-VBRDiscoveredComputerConfigurationPolicy -DiscoveredComputer <VBRDiscoveredComputer>  [<CommonParameters>] |

* Get the list of configuration options applied to computers in a protection group.

|  |
| --- |
| Get-VBRDiscoveredComputerConfigurationPolicy -ProtectionGroup <VBRProtectionGroup>  [<CommonParameters>] |

* Get the list of configuration options applied to protected computers using an ID of a configuration policy.

|  |
| --- |
| Get-VBRDiscoveredComputerConfigurationPolicy -Id <Guid>  [<CommonParameters>] |

|  |
| --- |
| Note |
| If you run the cmdlet with the DiscoveredComputer or ProtectionGroup parameter, the cmdlet returns only those configuration options that were applied with the specified parameter. For example, if you applied different configuration options to a computer with the DiscoveredComputer and ProtectionGroup parameters and you run the cmdlet with the DiscoveredComputer parameter, the cmdlet will return only configuration options applied with the DiscoveredComputer parameter. |

Detailed Description

This cmdlet returns the list of configuration options applied to individual computers or computers in a protection group using the [Add-VBRDiscoveredComputerConfigurationPolicy](add-vbrdiscoveredcomputerconfigurationpolicy.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DiscoveredComputer | Specifies an array of discovered computers. The cmdlet will return configuration options that were applied to the computers using this parameter. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md)[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True |
| ProtectionGroup | Specifies an array of protection groups. This cmdlet will return configuration options that were applied to computers in a protection group using this parameter. | Accepts the [VBRProtectionGroup](vbrprotectiongroup.md)[] object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True |
| Id | Specifies the ID of the configuration policy. | GUID | True | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDiscoveredComputerConfigurationPolicy](vbrdiscoveredcomputerconfigurationpolicy.md)

Examples

Viewing Settings Applied to Protection Group

This example shows how to return configuration options applied to computers that are members of the BackupServers protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "BackupServers"  Get-VBRDiscoveredComputerConfigurationPolicy -ProtectionGroup $group |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the Get-VBRDiscoveredComputerConfigurationPolicy cmdlet. Set the $group variable as the ProtectionGroup parameter value.

Related Commands

[Get-VBRProtectionGroup](get-vbrprotectiongroup.md)


