---
title: "Get-VBRViProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrviproxy.html"
last_updated: "4/18/2024"
product_version: "13.0.1.1071"
---

# Get-VBRViProxy


Short Description

Returns a list of VMware backup proxies.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRViProxy [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of VMware backup proxies managed by Veeam Backup & Replication.

Run the [Get-VBRJobProxy](get-vbrjobproxy.md) cmdlet to get the list of proxies assigned to a specific job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of VMware proxies. The cmdlet will return proxies with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CViProxy[] that contains an array of VMware backup proxy servers added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of VMware Backup Proxies

|  |  |
| --- | --- |
| This command gets a list of all VMware proxies managed by Veeam Backup & Replication.  |  | | --- | | Get-VBRViProxy | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting VMware Backup Proxy by Name

|  |  |
| --- | --- |
| This command gets the VMware backup proxy with the name LocalProxy.  |  | | --- | | Get-VBRViProxy -Name "LocalProxy" | |


