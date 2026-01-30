---
title: "Veeam Cloud Connect TLS Certificates"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/ssl_certificates.html"
last_updated: "7/21/2025"
product_version: "13.0.1.1071"
---

# Veeam Cloud Connect TLS Certificates


Veeam uses the TLS certificates to secure the TLS connection between the service provider and the user infrastructures. The service provider sets up a TLS certificate on the service provider side.

|  |
| --- |
| Important |
| With Veeam PowerShell, you cannot create a self-signed certificate or import a TLS certificate from file in the PFX format. You can only select an existing TLS certificate from the Microsoft Windows Certificates store. The certificate must be imported into the certificate store beforehand. |

| Cmdlet | Operation |
| --- | --- |
| [Generate-VBRCloudGatewayCertificate](generate-vbrcloudgatewaycertificate.md) | Creates a new self-signed TLS certificate for cloud gateways. |
| [Add-VBRCloudGatewayCertificate](add-vbrcloudgatewaycertificate.md) | Assigns the TLS certificate to the service provider. |
| [Get-VBRCloudGatewayCertificate](get-vbrcloudgatewaycertificate.md) | Returns the TLS certificates. |


