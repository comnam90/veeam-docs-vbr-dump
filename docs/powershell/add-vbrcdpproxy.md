---
title: "Add-VBRCDPProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcdpproxy.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCDPProxy


Short Description

Adds CDP proxies to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRCDPProxy -Server <CHost> [-Description <string>] [-CacheSize <uint32>] [-CacheSizeUnit {GB | TB}] [-CachePath <string>] [-SourceProxyTrafficPort <int>] [-TargetProxyTrafficPort <int>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds CDP proxies to the backup infrastructure. When you add a proxy, you assign the role of the CDP proxy to a Windows-based or Linux-based server. Note that the server to which you want to set a role of the CDP proxy, must be added to the backup infrastructure.

Run the [Add-VBRWinServer](add-vbrwinserver.md) cmdlet to add a Microsoft Windows server to the backup infrastructure or the [Add-VBRLinux](add-vbrlinux.md) cmdlet to add a Linux server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a server that you want to add as a CDP proxy. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Description | Specifies a description. The cmdlet will add a CDP proxy with this description. | String | False | Named | False |
| CacheSize | Specifies the cache size for a CDP proxy. | Uint32 | False | Named | False |
| CacheSizeUnit | For the CacheSize option.  Specifies the measure unit of the cache size. You can specify one of the following units:   * GB * TB   Default: GB. | VBRBackupCacheSizeUnit | False | Named | False |
| SourceProxyTrafficPort | Specifies a port number that a source host or cluster will use to communicate with a proxy. This parameter applies if the proxy that you configure acts as a source proxy.  Permitted values: 30332 to 30339.  Default: 33032.  Note: Do not provide the same port number for the source and target proxy. | Int32 | False | Named | False |
| TargetProxyTrafficPort | Specifies a port number that a source proxy will use to communicate with a target proxy. This parameter applies if the proxy that you configure acts as a target proxy.  Permitted values: 1 to 65535.  Default: 33033.  Note: Do not provide the same port number for the source and target proxy. | Int32 | False | Named | False |
| CachePath | Specifies a path to the folder where you want to keep a global cache.  Default:   * For Microsoft Windows servers: C:\VeeamCDP * For Linux servers: /VeeamCDP | String | False | Named | False |
| Force | Defines that the cmdlet will add a CDP proxy without showing warnings in the PowerShell console. | SwichParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPProxy object that contains CDP proxies to the backup infrastructure settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding CDP Proxy with Default Settings

|  |  |
| --- | --- |
| This example shows how to add the WindowsSRV05 server as a CDP proxy. The proxy will be added with the default settings:   * The cmdlet will run without showing any warning in the PowerShell console.  * The global cache is located in the C:\VeeamCDP folder.   |  | | --- | | $server = Get-VBRServer -Name "WindowsSRV05"  Add-VBRCDPProxy -Server $server -Description "CDPPRoxy05" -Force |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRCDPProxy cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Specify the Description parameter value. * Provide the Force parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding CDP Proxy with Custom Cache Settings

|  |  |
| --- | --- |
| This example shows how to add the WindowsSRV05 server as a CDP proxy. The proxy will be added with the custom global cache settings:   * The global cache size is set to 20 GB. * The global cache is located in the C:\CDPCache folder. * The cmdlet will run without showing any warning in the PowerShell console.   |  | | --- | | $server = Get-VBRServer -Name "WindowsSRV05"  Add-VBRCDPProxy -Server $server -Description "CDPPRoxy05" -CacheSize "20" -CachePath "C:\CDPCache" -Force |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRCDPProxy cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Specify the Description parameter value. * Specify the CacheSize parameter value. * Specify the CachePath parameter value. * Provide the Force parameter. |

Related Commands

[Get-VBRServer](get-vbrserver.md)


