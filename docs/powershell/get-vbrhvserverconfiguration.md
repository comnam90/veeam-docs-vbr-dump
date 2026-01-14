---
title: "Get-VBRHvServerConfiguration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrhvserverconfiguration.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Get-VBRHvServerConfiguration

In this article

Short Description

Returns settings of Microsoft Hyper-V hosts added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRHvServerConfiguration -Server <CHost>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the following settings of Microsoft Hyper-V hosts that are added to the backup infrastructure:

* EnableCBT: Specifies changed block tracking settings.

* If set to True, the changed block tracking option is enabled.
* If set to False, the changed block tracking option is disabled.

* EnableFailover: Specifies the failover option settings.

* If set to True, the failover option is enabled.
* If set to False, the failover option is disabled.
* Default: True.

* ServerId: Specifies the Microsoft Hyper-V hosts ID.

For more information on settings of Microsoft Hyper-V hosts that are added to the backup infrastructure, see the [Specify Settings for Connected Volumes](https://helpcenter.veeam.com/docs/vbr/userguide/hv_server_volumes.html?ver=13) section in the User Guide for Microsoft Hyper-V.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a Microsoft Hyper-V host added to the backup infrastructure. The cmdlet will return details about this Hyper-V host. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvServerConfiguration object that contains settings of Microsoft Hyper-V hosts added to the backup infrastructure.

Examples

Getting Settings of Microsoft Hyper-V Host

This example shows how to get settings of the hyperv09.tech.local Microsoft Hyper-V host that is added to the backup infrastructure.

|  |
| --- |
| $server = Get-VBRServer -Name hyperv09.tech.local  Get-VBRHvServerConfiguration -Server $server  EnableCBT                          EnableFailover ServerId  ---------                          -------------- --------      True                                    True 01e9fb70-42d8-4de3-b7ef-fcf7aa10cfaa |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the Get-VBRHvServerConfiguration cmdlet. Set the $server variable as the Server parameter value.

The cmdlet output will contain the following settings: EnableCBT, EnableFailover and ServerId.

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
