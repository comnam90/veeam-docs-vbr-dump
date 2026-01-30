---
title: "Add-VBRKMSServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrkmsserver.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-VBRKMSServer


Short Description

Adds KMS servers to the Veeam Backup & Replication console.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRKMSServer -CACertificate <X509Certificate2> -ClientCertificate <X509Certificate2> -Name <String> [-Description <String>] [-Port <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a Key Management System server (KMS server) to the Veeam Backup & Replication console.

For more information on working with KMS servers, see the Key Management System Keys section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Important |
| Before you run this cmdlet, you must get the certificate either from a file or from the certificates store. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CACertificate | Specifies the KMS server certificate. | X509Certificate2 | True | Named | False |
| ClientCertificate | Specifies the client certificate issued by the KMS administrator for Veeam Backup & Replication. | X509Certificate2 | True | Named | False |
| Name | Specifies the FQDN, IPv4 or IPv6 address of the KMS server. | String | True | Named | False |
| Description | Specifies description of the KMS server. | String | False | Named | False |
| Port | Specifies a port number to connect to the KMS server.  Default: 5696. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRKMSServer](vbrkmsserver.md)

Examples

Adding KMS Server to Veeam Backup & Replication Console

This command adds the thales.tech.local server to the Veeam Backup & Replication console.

|  |
| --- |
| Add-VBRKMSServer -Name "thales.tech.local" -Port 5696 -CACertificate $ClientCertificate -ClientCertificate $ClientCertificate |


