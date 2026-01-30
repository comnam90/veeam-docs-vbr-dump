---
title: "Set-VBRNetworkTrafficRuleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnetworktrafficruleoptions.html"
last_updated: "3/25/2024"
product_version: "13.0.1.1071"
---

# Set-VBRNetworkTrafficRuleOptions


Short Description

Modifies settings of global network traffic rules.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNetworkTrafficRuleOptions [-EnableMultipleUploadStreams] [-StreamsPerJobCount <Int32>] [-EnableIPv6]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of global network traffic rules.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| EnableMultipleUploadStreams | Enables multithreaded data transfer. | SwitchParameter | False | Named | False |
| StreamsPerJobCount | Specifies a number of TCP/IP transfer connection for every job session. | Int32 | False | Named | False |
| EnableIPv6 | Enables the IPv4/IPv6 dual stack mode is enabled or disabled. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNetworkTrafficRuleOptions](vbrnetworktrafficruleoptions.md)

Examples

Modifying Settings of Global Network Traffic Rules

This command enables multithreaded data transfer and sets a number of TCP/IP transfer connection for every job session to 8.

|  |
| --- |
| Set-VBRNetworkTrafficRuleOptions -EnableMultipleUploadStreams -StreamsPerJobCount 8 |


