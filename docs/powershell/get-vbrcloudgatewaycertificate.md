---
title: "Get-VBRCloudGatewayCertificate"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudgatewaycertificate.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudGatewayCertificate


Short Description

Returns TLS certificates.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRCloudGatewayCertificate [-FromStore]  [<CommonParameters>] |

Detailed Description

This cmdlet returns TLS certificates that are currently used, or the TLS certificate saved to your certificate store.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FromStore | Defines that the cmdlet will return the TLS certificate present in the local certificate store on this server. If you run the cmdlet without this parameter, it will return the certificate that is currently used. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudCertificate](vbrcloudcertificate.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting TLS Certificate from Certificate Store

|  |  |
| --- | --- |
| This command gets the Omega Company TLS certificate from the certificate store.  |  | | --- | | Get-VBRCloudGatewayCertificate -FromStore | Where FriendlyName -eq "Omega Company" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting TLS Certificate

|  |  |
| --- | --- |
| This command returns the TLS certificate that is currently assigned to the service provider.  |  | | --- | | Get-VBRCloudGatewayCertificate | |


