---
title: "Remove-VBRCloudVLANConfiguration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcloudvlanconfiguration.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCloudVLANConfiguration

In this article

Short Description

Removes pools of VLANs reserved for Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Remove-VBRCloudVLANConfiguration -Configuration <VBRCloudVLANConfiguration> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected VLAN pool.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Configuration | Specifies the VLAN configuration you want to remove. | Accepts the [VBRCloudVLANConfiguration](vbrcloudvlanconfiguration.md) object. To get this object, run the [Get-VBRCloudVLANConfiguration](get-vbrcloudvlanconfiguration.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Selected Pool of VLANs

This example shows how to remove a selected pool of VLANs.

|  |
| --- |
| $configs = Get-VBRCloudVLANConfiguration  Remove-VBRCloudVLANConfiguration -Configuration $configs[0] |

Perform the following steps:

1. Run the [Get-VBRCloudVLANConfiguration](get-vbrcloudvlanconfiguration.md) cmdlet. Save the array of pools to the $configs variable.

Mind the ordinal number of the necessary VLAN pool (in our example, it is the first VLAN pool in the array).

1. Run the Remove-VBRCloudVLANConfiguration cmdlet. Set the $configs variable as the Configuration parameter value.

Related Commands

[Get-VBRCloudVLANConfiguration](get-vbrcloudvlanconfiguration.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
