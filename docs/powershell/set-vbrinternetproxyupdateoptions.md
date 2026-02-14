---
title: "Set-VBRInternetProxyUpdateOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrinternetproxyupdateoptions.html"
last_updated: "2/13/2026"
product_version: "13.0.1.1071"
---

# Set-VBRInternetProxyUpdateOptions


Short Description

Modifies internet proxy update settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRInternetProxyUpdateOptions [-Enabled] [-ProxyServerName <String>] [-Port <Int32>] [-RequireAuthentication] [-Credentials <CCredentials>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies internet proxy update settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credentials | Specifies the credentials used to log in to the proxy server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Enabled | Enables the use of a proxy server. | SwitchParameter | False | Named | False |
| Port | Specifies the port used to connect to the proxy server. | Int32 | False | Named | False |
| ProxyServerName | Specifies the DNS or IP address of the proxy server. | String | False | Named | False |
| RequireAuthentication | Defines if the proxy server requires authentication. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRInternetProxyUpdateOptions

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting Proxy Server Without Authentication

|  |  |
| --- | --- |
| This command sets example.server.local as the proxy server for updates over port 443.  |  | | --- | | Set-VBRInternetProxyUpdateOptions -Enabled -ProxyServerName "example.server.local" -Port "443" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Proxy Server With Authentication

|  |  |
| --- | --- |
| This command sets example.server.local as the proxy server for updates over port 443. The command also provides credentials for authentication.  |  | | --- | | $creds = Get-VBRCredentials  Set-VBRInternetProxyUpdateOptions -Enabled -ProxyServerName "example.server.local" -Port "443" -RequireAuthentication -Credentials $creds |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $creds variable. 2. Run the Set-VBRInternetProxyUpdateOptions cmdlet and specify the following settings:  * Specify the ProxyServerName parameter value. * Specify the Port parameter value. * Set the $creds variable as the Credentials parameter value. |

Related Commands

[Get-VBRInternetProxyUpdateOptions](get-vbrinternetproxyupdateoptions.md)


