---
title: "Deploying Settings to Veeam Agent Computers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/how_to_deploy_settings.html"
last_updated: "11/26/2025"
product_version: "13.0.1.1071"
---

# Deploying Settings to Veeam Agent Computers

In this article

If you want to automate application of Veeam Agent settings to protected computers, you can use the Veeam Backup PowerShell module. For more information about the module, see the [Veeam PowerShell Reference](https://helpcenter.veeam.com/docs/vbr/powershell/getting_started.html?ver=13).

|  |
| --- |
| IMPORTANT |
| Make sure that you have tested the cmdlets described in this section in a test lab before their execution in the production environment. Operations performed with these cmdlets can cause data loss, and you will not be able to undo changes. |

Deploying Settings

To deploy settings to managed computers, perform the following steps:

1. Start a Veeam PowerShell session. For more information, see the [Running Veeam Backup PowerShell Sessions](https://helpcenter.veeam.com/docs/vbr/powershell/running_sessions.html?ver=13) in the Veeam PowerShell Reference.
2. Create a new configuration option for Veeam Agent settings using the New-VBRDiscoveredComputerConfigurationOption cmdlet. For more information, see the [New-VBRDiscoveredComputerConfigurationOption](https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrdiscoveredcomputerconfigurationoption.html?ver=13) section in the Veeam PowerShell Reference.
3. Add the created configuration option to a configuration policy and assign the configuration policy to a protected computer or a protection group using the Add-VBRDiscoveredComputerConfigurationPolicy cmdlet. For more information, see the [Add-VBRDiscoveredComputerConfigurationPolicy](https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrdiscoveredcomputerconfigurationpolicy.html?ver=13) section in the Veeam PowerShell Reference.
4. Rescan the protection group to apply new settings. For more information, see [Rescanning Protection Group](agents_protection_group_rescan.md).

Checking Current Settings

To check what settings are applied to managed computers, use the Get-VBRDiscoveredComputerConfigurationPolicy cmdlet. For more information, see the [Get-VBRDiscoveredComputerConfigurationPolicy](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdiscoveredcomputerconfigurationpolicy.html?ver=13) section in the Veeam PowerShell Reference.

Deleting Settings

To delete a configuration policy that contains a configuration option for Veeam Agent settings, use the the Remove-VBRDiscoveredComputerConfigurationPolicy cmdlet. For more information, see the [Remove-VBRDiscoveredComputerConfigurationPolicy](https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrdiscoveredcomputerconfigurationpolicy.html?ver=13) section in the Veeam PowerShell Reference.

|  |
| --- |
| IMPORTANT |
| Consider the following:   * Before you apply other settings to Veeam Agent computers, make sure to delete the currently applied configuration policy with the Remove-VBRDiscoveredComputerConfigurationPolicy cmdlet. Otherwise, the policy settings will be reapplied after the rescan of the protected computer or protection group. * The removal of the configuration policy does not update settings on Veeam Agent computers to which the policy has been applied. If you want to update the settings, you must create a new policy and assign it to discovered computers using the Add-VBRDiscoveredComputerConfigurationPolicy cmdlet. For more information, see the [Add-VBRDiscoveredComputerConfigurationPolicy](https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrdiscoveredcomputerconfigurationpolicy.html?ver=13) section in the Veeam PowerShell Reference. |

Page updated 11/26/2025

Page content applies to build 13.0.1.1071
