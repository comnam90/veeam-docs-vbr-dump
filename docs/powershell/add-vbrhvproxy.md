---
title: "Add-VBRHvProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhvproxy.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Add-VBRHvProxy


Short Description

Adds a Hyper-V backup proxy to the backup infrastructure.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRHvProxy -Server <CHost> [-Description <String>] [-MaxTasks <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a Hyper-V backup proxy server to the backup infrastructure.

When you add a proxy, you set a role to a Microsoft Windows server. To add a new proxy, you need to have the server added to your Veeam Backup & Replication managing console.

Run the [Add-VBRWinServer](add-vbrwinserver.md) cmdlet to add a Microsoft Windows server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a server which will act as a Hyper-V backup proxy. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| Description | Specifies a description of a Hyper-V backup proxy. | String | False | Named | False |
| MaxTasks | Specifies the number of concurrent tasks that can be assigned to the proxy simultaneously.  Allowed values: 1-100.  Default: 2. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHvProxy[] that contains an array of Hyper-V backup proxy servers added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding New Hyper-V Backup Proxy [Using Variable]

|  |  |
| --- | --- |
| This example shows how to add a new Hyper-V backup proxy. The description is Local Backup Proxy. The max concurrent tasks number is set to 2 by default.  |  | | --- | | $server = Get-VBRServer -Name "Server"  Add-VBRHvProxy -Server $server -Description "Local Backup Proxy" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRHvProxy cmdlet. Set the $server variable as the Server parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding New Hyper-V Backup Proxy [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to add a new Hyper-V backup proxy. The description is Local Backup Proxy. The max concurrent tasks number is set to 6.  |  | | --- | | Get-VBRServer -Name "HyperV Local Server" | Add-VBRHvProxy -Description "Local Backup Proxy" -MaxTasks 6 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Add-VBRHvProxy cmdlet. Specify the Description parameter value. Specify the MaxTasks parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)


