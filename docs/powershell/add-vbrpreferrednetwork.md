---
title: "Add-VBRPreferredNetwork"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrpreferrednetwork.html"
last_updated: "2/9/2024"
product_version: "13.0.1.1071"
---

# Add-VBRPreferredNetwork

In this article

Short Description

Specifies preferred networks.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRPreferredNetwork -IpAddress <ipaddress> -SubnetMask <string>  [<CommonParameters>] |

Detailed Description

This cmdlet specifies preferred networks for the backup infrastructure. You can instruct Veeam Backup & Replication to transfer data over preferred networks only. To do that, run the [Enable-VBRPreferredNetworkDataTransfer](enable-vbrpreferrednetworkdatatransfer.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| IpAddress | Specifies the IP address for a preferred network. | IPAddress | True | Named | True (ByPropertyName) |
| SubnetMask | Specifies the subnet mask for a preferred network. | String | True | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRPreferredNetwork](vbrpreferrednetwork.md)

Examples

Adding Preferred Network to List

This command adds the a preferred network to a list of preferred networks.

|  |
| --- |
| Add-VBRPreferredNetwork -IpAddress 192.168.0.1 -SubnetMask 255.255.255.255 |

Page updated 2/9/2024

Page content applies to build 13.0.1.1071
