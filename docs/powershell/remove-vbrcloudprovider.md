---
title: "Remove-VBRCloudProvider"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcloudprovider.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCloudProvider

In this article

Short Description

Removes service providers.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Remove-VBRCloudProvider -CloudProvider <VBRCloudProvider[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes service provider from Veeam Backup & Replication.

When you remove a service provider, you become unable to reach your cloud repository. The data stored on the cloud repository remains. You can access it if you add the service provider to the Veeam backup console again.

|  |
| --- |
| Important |
| The CCredentials type object for the Credentials parameter is not accepted any longer. Run the [Add-VBRCloudProviderCredentials](add-vbrcloudprovidercredentials.md) cmdlet to specify the cloud provider credentials records. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Cloud | Specifies the array of cloud providers you want to remove. | Accepts the [VBRCloudProvider[]](vbrcloudprovider.md) object. To get this object, run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing All Cloud Service Providers [Using Pipeline]

|  |  |
| --- | --- |
| This command removes all cloud service providers added to Veeam Backup & Replication. The service providers are obtained by the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet and piped down.  |  | | --- | | Get-VBRCloudProvider | Remove-VBRCloudProvider | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Cloud Service Provider [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove a selected service provider.  |  | | --- | | $CloudProvider1 = Get-VBRCloudProvider -Name "104.45.95.227"  Remove-VBRCloudProvider -CloudProvider $CloudProvider1 |  Perform the following steps:   1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. Save the result to the $CloudProvider1 variable. 2. Run the Remove-VBRCloudProvider cmdlet. Set the $CloudProvider1 variable as the CloudProvider parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing All Cloud Service Providers [Using Pipeline]

|  |  |
| --- | --- |
| This command removes a service provider with the 104.45.95.227 IP address. The service provider is obtained by the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet and piped down.  |  | | --- | | Get-VBRCloudProvider -Name "104.45.95.227" | Remove-VBRCloudProvider | |

Related Commands

[Get-VBRCloudProvider](get-vbrcloudprovider.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
