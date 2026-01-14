---
title: "Get-VBRCloudGatewayPool"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudgatewaypool.html"
last_updated: "4/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCloudGatewayPool

In this article

Short Description

Returns cloud gateway pools.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all cloud gateway pools.

|  |
| --- |
| Get-VBRCloudGatewayPool  [<CommonParameters>] |

* Get cloud gateway pools by the cloud gateway pool ID.

|  |
| --- |
| Get-VBRCloudGatewayPool [-Id <Guid[]>]  [<CommonParameters>] |

* Get the cloud gateway pools by the cloud gateway pool name.

|  |
| --- |
| Get-VBRCloudGatewayPool [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing cloud gateway pools.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for cloud gateway pools that you want to get. | Guid[] | True | Named | True (ByValue) |
| Name | Specifies an array of names for cloud gateway pool that you want to get. | String[] | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudGatewayPool](vbrcloudgatewaypool.md)[]

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cloud Gateway Pools

|  |  |
| --- | --- |
| This command gets all cloud gateway pools.  |  | | --- | | Get-VBRCloudGatewayPool | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Gateway Pool by Name

|  |  |
| --- | --- |
| This command gets the CloudGT01 cloud gateway pool by the cloud gateway pool name.  |  | | --- | | Get-VBRCloudGatewayPool -Name "CloudGT01" | |

Page updated 4/12/2024

Page content applies to build 13.0.1.1071
