---
title: "Get-VBRNetworkTrafficRuleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnetworktrafficruleoptions.html"
last_updated: "1/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNetworkTrafficRuleOptions


Short Description

Returns settings of global network traffic rules.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRNetworkTrafficRuleOptions |

Detailed Description

This cmdlet returns the following settings of global network traffic rules:

* MultipleUploadStreamsEnabled — Defines that multithreaded data transfer is enabled or disabled.
* StreamsPerJobCount — Specifies a number of TCP/IP transfer connection for every job session.
* IPv6Enabled —  Defines that the IPv4/IPv6 dual stack mode is enabled or disabled.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNetworkTrafficRuleOptions](vbrnetworktrafficruleoptions.md)

Examples

Getting Settings of Global Network Traffic Rules

This command returns the following settings of global network traffic rules: MultipleUploadStreamsEnabled, StreamsPerJobCount and IPv6Enabled.

|  |
| --- |
| Get-VBRNetworkTrafficRuleOptions |


