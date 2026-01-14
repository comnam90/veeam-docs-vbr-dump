---
title: "Add-VBRComputerFileProxyServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcomputerfileproxyserver.html"
last_updated: "8/6/2025"
product_version: "13.0.1.1071"
---

# Add-VBRComputerFileProxyServer

In this article

Short Description

Adds general-purpose backup proxies to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRComputerFileProxyServer -Server <CHost> [-Description <string>] [-ConcurrentTaskNumber <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds general-purpose backup proxies to the backup infrastructure. To learn about general-purpose backup proxies, see the [General-Purpose Backup Proxies](https://helpcenter.veeam.com/docs/vbr/userguide/backup_proxy_general.html?ver=13) section in the Veeam Backup & Replication User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the host where the general-purpose backup proxy is located. The cmdlet will add this host as the general-purpose backup proxy to the backup infrastructure.  Note: The cmdlet can only add general-purpose backup proxies that run the Microsoft Windows Server OS. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, |
| Description | Specifies a description of the general-purpose backup proxy. The cmdlet will add the general-purpose backup proxy with the specified description. | String | False | Named | False |
| ConcurrentTaskNumber | Specifies a number of concurrent tasks that can be assigned to the general-purpose backup proxy simultaneously.  Permitted values: 1-128.  Default: 2. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerFileProxyServer object that contains settings of the general-purpose backup proxy added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding General-purpose Backup Proxies

|  |  |
| --- | --- |
| This example shows how to add a general-purpose backup proxy to the backup infrastructure. The general-purpose backup proxy is assigned two concurrent tasks to process.  |  | | --- | | $server = Get-VBRServer -Name "File Proxy 01"  Add-VBRComputerFileProxyServer -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRComputerFileProxyServer cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding General-purpose Backup Proxies with Specific Number of Concurrent Tasks

|  |  |
| --- | --- |
| This example shows how to add general-purpose backup proxies to the backup infrastructure. The general-purpose backup proxy is assigned 100 concurrent tasks to process.  |  | | --- | | $server = Get-VBRServer -Name "File Proxy 01"  Add-VBRComputerFileProxyServer -Server $server -ConcurrentTaskNumber 100 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRComputerFileProxyServer cmdlet. Set the $server variable as the Server parameter value. Specify the ConcurrentTaskNumber parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 8/6/2025

Page content applies to build 13.0.1.1071
