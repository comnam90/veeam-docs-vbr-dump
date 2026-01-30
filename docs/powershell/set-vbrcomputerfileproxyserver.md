---
title: "Set-VBRComputerFileProxyServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputerfileproxyserver.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Set-VBRComputerFileProxyServer


Short Description

Modifies general-purpose backup proxies added to the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRComputerFileProxyServer -FileProxy <VBRComputerFileProxyServer> [-Description <string>] [-ConcurrentTaskNumber <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an existing general-purpose backup proxy.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FileProxy | Specifies the general-purpose backup proxy. The cmdlet will modify the settings of this proxy. | Accepts the VBRComputerFileProxyServer object. To get this object, run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Description | Specifies a description of the general-purpose backup proxy. The cmdlet will add the backup proxy with the specified description. | String | False | Named | False |
| ConcurrentTaskNumber | Specifies the integer defining the number of concurrent tasks that can be assigned to the backup proxy simultaneously.  Permitted values: 1-128.  Default: 2. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerFileProxyServer object that contains settings of the general-purpose backup proxy added to the Veeam Backup & Replication infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Description

|  |  |
| --- | --- |
| This example shows how to modify a description of the general-purpose backup proxy.  |  | | --- | | $proxy = Get-VBRComputerFileProxyServer -Name "File Proxy 01"  Set-VBRComputerFileProxyServer -FileProxy $proxy -Description "Proxy for Veeam Agents" |  Perform the following steps:   1. Run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the Set-VBRComputerFileProxyServer cmdlet. Set the $proxy variable as the FileProxy parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Number of Concurrent Tasks

|  |  |
| --- | --- |
| This example shows how to modify the number of concurrent tasks for the general-purpose backup proxy. The general-purpose backup proxy will process 50 concurrent tasks simultaneously.  |  | | --- | | $proxy = Get-VBRComputerFileProxyServer -Name "File Proxy 01"  Set-VBRComputerFileProxyServer -FileProxy $proxy -ConcurrentTaskNumber 50 |  Perform the following steps:   1. Run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the Set-VBRComputerFileProxyServer cmdlet. Set the $proxy variable as the FileProxy parameter value. Specify the ConcurrentTaskNumber parameter value. |

Related Commands

[Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md)


