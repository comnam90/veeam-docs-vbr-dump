---
title: "Generate-VBRCloudGatewayCertificate"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/generate-vbrcloudgatewaycertificate.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# Generate-VBRCloudGatewayCertificate


Short Description

Creates a new self-signed TLS certificate for cloud gateways.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Generate-VBRCloudGatewayCertificate [-FriendlyName <String>] [-Subject <String>] [-ValidForDays <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>] |

Detailed Description

This cmdlet creates a certificate that secures traffic between tenant components and cloud gateways. After you generate the certificate, the cmdlet will save it to the local computer certificate store.

To assign the certificate to the cloud gateways, run the [Add-VBRCloudGatewayCertificate](add-vbrcloudgatewaycertificate.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FriendlyName | Specifies a name that you want to assign to the certificate. | String | False | Named | False |
| Subject | Specifies the certificate subject in FQDN format.  Default: CN=Veeam Software, O=Veeam Software, OU=Veeam Software. | String | False | Named | False |
| ValidForDays | Specifies the number of days during which the certificate will remain valid.  Default: 365 days. | Int32 | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCloudGatewayCertificate object that defines the certificate settings.

Examples

Generating Certificate for Cloud Gateways

This command creates a certificate with the following settings:

* The certificate is vaild for 2 years.
* The certificate is generated for cloudgw.tech.com.
* The friendly name is "Gateway-25".

|  |
| --- |
| Generate-VBRCloudGatewayCertificate ‑FriendlyName "CC-GW-2024" ‑Subject "cloudgw.tech.com" ‑ValidForDays 730 |


