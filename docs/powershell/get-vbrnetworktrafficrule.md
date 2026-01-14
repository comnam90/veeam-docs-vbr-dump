---
title: "Get-VBRNetworkTrafficRule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnetworktrafficrule.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNetworkTrafficRule

In this article

Short Description

Returns network traffic rules.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get network traffic rules by the network traffic rule name

|  |
| --- |
| Get-VBRNetworkTrafficRule [-Name <string[]>]  [<CommonParameters>] |

* Get network traffic rules by the network traffic rule ID

|  |
| --- |
| Get-VBRNetworkTrafficRule [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of network traffic rules.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names. The cmdlet will return network traffic rules with the specified names. | String[] | False | Named | False |
| Id | Specifies an array of IDs. The cmdlet will return network traffic rules with the specified IDs. | GUID[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNetworkTrafficRule](vbrnetworktrafficrule.md)

Examples

Getting Network Traffic Rule by Name

This command gets a network traffic rule by the network traffic rule name.

|  |
| --- |
| Get-VBRNetworkTrafficRule -Name "New rule" |

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
