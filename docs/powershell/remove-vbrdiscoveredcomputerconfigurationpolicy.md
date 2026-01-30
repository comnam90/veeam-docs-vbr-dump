---
title: "Remove-VBRDiscoveredComputerConfigurationPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrdiscoveredcomputerconfigurationpolicy.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRDiscoveredComputerConfigurationPolicy


Short Description

Removes policies that contain configuration options for Veeam Agent settings.

|  |
| --- |
| Important |
| Make sure to test this cmdlet in the lab before you run it in the production environment. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRDiscoveredComputerConfigurationPolicy -Policy <VBRDiscoveredComputerConfigurationPolicy[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes policies that contain configuration options for Veeam Agent settings.

|  |
| --- |
| Important |
| The cmdlet does not update settings on discovered computers to which the policy has been applied. If you want to change the settings, you must create a new policy and assign it to discovered computers. To create a new policy, run the [Add-VBRDiscoveredComputerConfigurationPolicy](add-vbrdiscoveredcomputerconfigurationpolicy.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies the policy that you want to remove. | Accepts the [VBRDiscoveredComputerConfigurationPolicy](vbrdiscoveredcomputerconfigurationpolicy.md)[] object. To get this object, run the [Get-VBRDiscoveredComputerConfigurationPolicy](get-vbrdiscoveredcomputerconfigurationpolicy.md) cmdlet. | True | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParamter | False | Named | False |
| Confirm | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Policy

This example shows how to remove a policy using the policy ID.

|  |
| --- |
| $PolicyToRemove = Get-VBRDiscoveredComputerConfigurationPolicy -Id a78eceb5-d5b8-4fe0-9a8c-cc788a123c4a  Remove-VBRDiscoveredComputerConfigurationPolicy -Policy $PolicyToRemove |

Perform the following steps:

1. Run the [Get-VBRDiscoveredComputerConfigurationPolicy](get-vbrdiscoveredcomputerconfigurationpolicy.md) cmdlet. Specify the Id parameter value. Save the result to the $PolicyToRemove variable.
2. Run the Remove-VBRDiscoveredComputerConfigurationPolicy cmdlet. Set the $PolicyToRemove variable as the Policy parameter value.

Related Commands

* [New-VBRDiscoveredComputerConfigurationOption](new-vbrdiscoveredcomputerconfigurationoption.md)
* [Add-VBRDiscoveredComputerConfigurationPolicy](add-vbrdiscoveredcomputerconfigurationpolicy.md)
* [Get-VBRDiscoveredComputerConfigurationPolicy](get-vbrdiscoveredcomputerconfigurationpolicy.md)


