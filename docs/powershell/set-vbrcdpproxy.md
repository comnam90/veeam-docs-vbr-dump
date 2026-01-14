---
title: "Set-VBRCDPProxy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcdpproxy.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCDPProxy

In this article

Short Description

Modifies settings of CDP proxies added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCDPProxy -Proxy <VBRCDPProxy> [-Description <string>] [-CacheSize <uint32>] [-CacheSizeUnit <VBRBackupCacheSizeUnit>] [-CachePath <string>] [-SourceProxyTrafficPort <int>] [-TargetProxyTrafficPort <int>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of CDP proxies added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies a CDP proxy. The cmdlet will modify the settings of this proxy. | Accepts the VBRCDPProxy object. To create this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Description | Specifies a description for a CDP proxy. | String | False | Named | False |
| CacheSize | Specifies the cache size for a CDP proxy.  Note: When you specify the cache size, keep in mind the following recommendations:   * You need to allocate 1 GB for each protected VM.  * You need to leave 10 percent of the proxy storage free. | Uint32 | False | Named | False |
| CacheSizeUnit | For the CacheSize option.  Specifies the measure unit of the cache size. You can specify one of the following units:   * GB * TB   Default: GB. | VBRBackupCacheSizeUnit | False | Named | False |
| CachePath | Specifies a path to the folder where you want to keep a global cache.  Default:   * For Microsoft Windows servers: C:\VeeamCDP * For Linux servers: /VeeamCDP | String | False | Named | False |
| SourceProxyTrafficPort | Specifies the port number of the source proxy. | Int | False | Named | False |
| TargetProxyTrafficPort | Specifies the port number of the target proxy. | Int | False | Named | False |
| Force | Defines that the cmdlet will modify a CDP proxy without showing warnings in the PowerShell console. | SwichParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPProxy object that contains CDP proxies to the backup infrastructure settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying CDP Proxy Cache Size

|  |  |
| --- | --- |
| This example shows how to modify a size of the cache that is used by the Proxy05 CDP proxy.  |  | | --- | | $proxy = Get-VBRCDPProxy -Name "Proxy05"  Set-VBRCDPProxy -Proxy $proxy -CacheSize "25" |  Perform the following steps:   1. Run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the Set-VBRCDPProxy cmdlet. Set the $proxy variable as the Proxy parameter value. Specify the CacheSize parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying CDP Proxy Cache Location

|  |  |
| --- | --- |
| This example shows how to modify a path to the folder where the Proxy05 CDP proxy keeps the cache.  |  | | --- | | $proxy = Get-VBRCDPProxy -Name "Proxy05"  Set-VBRCDPProxy -Proxy $proxy -CachePath "C:\CacheFolder" |  Perform the following steps:   1. Run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the Set-VBRCDPProxy cmdlet. Set the $proxy variable as the Proxy parameter value. Specify the CachePath parameter value. |

Related Commands

[Get-VBRCDPProxy](get-vbrcdpproxy.md)

Page updated 10/16/2025

Page content applies to build 13.0.1.1071
