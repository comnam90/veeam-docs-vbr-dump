---
title: "Set-VBRHvServerConfiguration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvserverconfiguration.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRHvServerConfiguration

In this article

Short Description

Modifies settings of Microsoft Hyper-V hosts added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRHvServerConfiguration -Configuration <VBRHvServerConfigurationObject[]> [-EnableFailover] [-EnableCBT]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Microsoft Hyper-V hosts added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Configuration | Specifies an array of settings of Microsoft Hyper-V hosts. The cmdlet will modify these settings. | Accepts the VBRHvServerConfigurationObject[] object. To create this object, run the [Get-VBRHvServerConfiguration](get-vbrhvserverconfiguration.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| EnableFailover | Defines that the cmdlet will enable the failover option settings.  If you do not provide this parameter, Veeam Backup & Replication will fail over to a software VSS provider when the hardware VSS provider does not manage to create a volume snapshot.  Default: False. | SwitchParameter | False | Named | True (ByValue, ByPropertyName) |
| EnableCBT | Defines that the cmdlet will enable the changed block tracking option for processing the Microsoft Hyper-V VMs.  If you do not provide this parameter, the changed block tracking option will not be enabled.  Default: False. | SwitchParameter | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvServerConfiguration object that contains settings of Microsoft Hyper-V hosts added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Failover Options for Microsoft Hyper-V Host

|  |  |
| --- | --- |
| This example shows how to enable the failover option for the hyperv09.tech.local Microsoft Hyper-V host added to the backup infrastructure.  |  | | --- | | $server = Get-VBRServer -Name hyperv09.tech.local  $settings = Get-VBRHvServerConfiguration -Server $server  Set-VBRHvServerConfiguration -Configuration $settings -EnableFailover |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerConfiguration](get-vbrhvserverconfiguration.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $settings variable. 3. Run the Set-VBRHvServerConfiguration cmdlet. Set the $settings variable as the Configuration parameter value. Provide the EnableFailover parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling Changed Block Tracking Option for Microsoft Hyper-V Host

|  |  |
| --- | --- |
| This example shows how to enable the changed block tracking for processing the hyperv09.tech.local Microsoft Hyper-V host added to the backup infrastructure.  |  | | --- | | $server = Get-VBRServer -Name hyperv09.tech.local  $settings = Get-VBRHvServerConfiguration -Server $server  Set-VBRHvServerConfiguration -Configuration $settings -EnableCBT |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerConfiguration](get-vbrhvserverconfiguration.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $settings variable. 3. Run the Set-VBRHvServerConfiguration cmdlet. Set the $settings variable as the Configuration parameter value. Provide the EnableCBT parameter. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRHvServerConfiguration](get-vbrhvserverconfiguration.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
