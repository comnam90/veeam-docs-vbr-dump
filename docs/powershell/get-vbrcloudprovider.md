---
title: "Get-VBRCloudProvider"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudprovider.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudProvider

In this article

Short Description

Returns service providers.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all cloud service providers.

|  |
| --- |
| Get-VBRCloudProvider  [<CommonParameters>] |

* Get cloud service providers by ID.

|  |
| --- |
| Get-VBRCloudProvider [-Id <guid[]>]  [<CommonParameters>] |

* Get cloud service providers by name.

|  |
| --- |
| Get-VBRCloudProvider [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns service providers added to Veeam Backup & Replication.

You can get the list of all existing service providers or search for instances directly by name or ID.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the array of the cloud provider IDs you want to get. | Accepts GUID[] or string[]. | False | Named | True (ByValue, |
| Name | Specifies the array of the service provider names you want to get or search conditions. | String[] | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudProvider[]](vbrcloudprovider.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cloud Service Providers

|  |  |
| --- | --- |
| This command returns all cloud service providers added to Veeam Backup & Replication.  |  | | --- | | Get-VBRCloudProvider | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Service Provider by IP Address

|  |  |
| --- | --- |
| This command looks for the cloud service provider with the 104.45.95.227 IP address.  |  | | --- | | Get-VBRCloudProvider -Name "104.45.95.227" | |

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
