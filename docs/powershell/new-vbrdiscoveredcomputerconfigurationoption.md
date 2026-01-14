---
title: "New-VBRDiscoveredComputerConfigurationOption"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrdiscoveredcomputerconfigurationoption.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# New-VBRDiscoveredComputerConfigurationOption

In this article

Short Description

Creates new configuration options for Veeam Agent settings.

|  |
| --- |
| Important |
| Make sure to test this cmdlet in the lab before you run it in the production environment. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRDiscoveredComputerConfigurationOption -Name <string> -Value <Object>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRDiscoveredComputerConfigurationOption](vbrdiscoveredcomputerconfigurationoption.md) object. This object contains new configuration options for Veeam Agent settings that you can distribute to discovered computers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name that you want to assign to a new configuration option. | String | True | Named | True |
| Value | Specifies a value that the configuration option must store. | Object | True | Named | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDiscoveredComputerConfigurationOption](vbrdiscoveredcomputerconfigurationoption.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Allowing File-Level Restore Without Administrator Privileges on Windows Computers

|  |  |
| --- | --- |
| This command creates a new entry of the REG\_DWORD type for the EnableUserFLR registry value on Microsoft Windows computers.  |  | | --- | | New-VBRDiscoveredComputerConfigurationOption -Name EnableUserFLR -Value 1 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restricting VPN Connections Usage on Windows Computers

|  |  |
| --- | --- |
| This command creates a new entry of the REG\_MULTI\_SZ type for the RestrictVpnNetworkAdapters registry value on Microsoft Windows computers.  |  | | --- | | New-VBRDiscoveredComputerConfigurationOption -Name RestrictVpnNetworkAdapters -Value @(“Cisco AnyConnect Secure Mobility Client Virtual Miniport Adapter for Windows”, “Fortinet Virtual Ethernet Adapter”,“TAP-Windows Adapter”) | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Job Queue Maximum Capacity on Linux and Mac Computers

|  |  |
| --- | --- |
| This command creates a new entry for the JobQueueCapacity value in the configuration file on Mac and Linux computers.  |  | | --- | | New-VBRDiscoveredComputerConfigurationOption -Name “general.JobQueueCapacity” -Value 4 | |

Related Commands

* [Add-VBRDiscoveredComputerConfigurationPolicy](add-vbrdiscoveredcomputerconfigurationpolicy.md)
* [Get-VBRDiscoveredComputerConfigurationPolicy](get-vbrdiscoveredcomputerconfigurationpolicy.md)
* [Remove-VBRDiscoveredComputerConfigurationPolicy](remove-vbrdiscoveredcomputerconfigurationpolicy.md)

Page updated 6/3/2024

Page content applies to build 13.0.1.1071
