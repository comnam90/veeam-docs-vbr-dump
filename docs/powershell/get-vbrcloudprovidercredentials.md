---
title: "Get-VBRCloudProviderCredentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudprovidercredentials.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudProviderCredentials

In this article

Short Description

Returns an array of cloud provider credentials records added to Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an array of cloud provider credential records by the tenant name.

|  |
| --- |
| Get-VBRCloudProviderCredentials [-Name <string[]>]  [<CommonParameters>] |

* Get an array of cloud provider credential records by the credentials records ID.

|  |
| --- |
| Get-VBRCloudProviderCredentials -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of cloud provider credentials records.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the login for cloud provider credentials records. The cmdlet will return credentials records with the specified name. | String[] | False | Named | False |
| Id | Specifies the ID for cloud provider credentials records. The cmdlet will return credentials records with the specified ID. | GUID[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRCloudProviderCredentials

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Cloud Provider Credentials by Tenant Name

|  |  |
| --- | --- |
| This example shows how to get cloud provider credentials records by the tenant name.  |  | | --- | | Get-VBRCloudProviderCredentials -Name "Tenant1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Provider Credentials by ID

|  |  |
| --- | --- |
| This example shows how to get cloud provider credentials records by the credentials records ID.  |  | | --- | | Get-VBRCloudProviderCredentials -ID "bea3b786-75de-4882-a4f7-c2f236eb2874" | |

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
