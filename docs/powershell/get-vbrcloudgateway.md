---
title: "Get-VBRCloudGateway"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudgateway.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudGateway

In this article

Short Description

Returns cloud gateways.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all cloud gateways.

|  |
| --- |
| Get-VBRCloudGateway  [<CommonParameters>] |

* Get the cloud gateways by ID.

|  |
| --- |
| Get-VBRCloudGateway [-Id <Guid[]>]  [<CommonParameters>] |

* Get the cloud gateways by name.

|  |
| --- |
| Get-VBRCloudGateway [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing cloud gateways.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the array of IDs of cloud gateways. | Accepts GUID[] or string[]. | False | Named | True (ByValue, |
| Name | Specifies the array of the cloud gateway names you want to get or search conditions. | String[] | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudGateway[]](vbrcloudgateway.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cloud Gateways

|  |  |
| --- | --- |
| This command returns all cloud gateways configured in Veeam Backup & Replication.  |  | | --- | | Get-VBRCloudGateway | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Gateway by Name

|  |  |
| --- | --- |
| This command gets the cloud gateway by name.  |  | | --- | | Get-VBRCloudGateway -Name "Cloud gateway" | |

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
