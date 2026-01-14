---
title: "Get-VBRCDPPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcdppolicy.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCDPPolicy

In this article

Short Description

Returns CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get CDP policies by their names.

|  |
| --- |
| Get-VBRCDPPolicy [-Name <string[]>]  [<CommonParameters>] |

* Get CDP policies by their IDs.

|  |
| --- |
| Get-VBRCDPPolicy [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies, universal CDP policies and so on.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of policies. The cmdlet will return a list of policies with these names. | String[] | False | Named | True (ByValue, ByPropertyName) |
| Id | Specifies an array of IDs of policies. The cmdlet will return a list of policies with the specified IDs. | Guid[] | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPPolicyBase[] object that defines settings of CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting CDP Policy by Name

|  |  |
| --- | --- |
| This command returns the VM079 CDP policy.  |  | | --- | | Get-VBRCDPPolicy -Name "VM079" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting CDP Policy by ID

|  |  |
| --- | --- |
| This command returns the 13744fce-e8ea-4b77-9092-26e3f09e6a6e CDP policy.  |  | | --- | | Get-VBRCDPPolicy -Id "13744fce-e8ea-4b77-9092-26e3f09e6a6e" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting all CDP Policies

|  |  |
| --- | --- |
| This command returns all CDP policies that are created on the backup server.  |  | | --- | | Get-VBRCDPPolicy | |

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
