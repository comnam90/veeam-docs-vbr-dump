---
title: "Add-VBRCloudPublicIP"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcloudpublicip.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCloudPublicIP

In this article

Short Description

Adds public IP address or a pool of IP addresses.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Add-VBRCloudPublicIP -FirstIpAddress <ipaddress> [-LastIpAddress <ipaddress>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a single IP address or a range of IP addresses to the public IP address pool. You can create a pool of public IP addresses and provide them to tenants. The tenants will be able to connect their replicas to your network so that the replicas are accessible from the Internet during a full site failover.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FirstIpAddress | Specifies a single IP address or the first IP address of the range that you want to add. | IPAddress | True | Named | True (ByValue) |
| LastIpAddress | Specifies the last IP address of the range that you want to add. | IPAddress | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudIP](vbrcloudip.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Pool of Public IP Addresses

|  |  |
| --- | --- |
| This command creates a pool of public IP addresses.  |  | | --- | | Add-VBRCloudPublicIP -FirstIpAddress 198.51.100.1 -LastIpAddress 198.51.100.15 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Public IP Address

|  |  |
| --- | --- |
| This command adds an individual public IP address.  |  | | --- | | Add-VBRCloudPublicIP -FirstIpAddress 198.51.100.17 | |

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
