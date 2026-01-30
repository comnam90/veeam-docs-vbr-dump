---
title: "VBRKMSServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrkmsserver.html"
last_updated: "7/25/2024"
product_version: "13.0.1.1071"
---

# VBRKMSServer


Contains KMS server settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | Guid | KMS server id. |
| Name | String | KMS server name. |
| Port | Int32 | KMS server port. |
| CACertificate | X509Certificate2 | KMS server server certificate. |
| ClientCertificate | X509Certificate2 | Client certificate. |
| Description | String | KMS server description. |

Related Commands

* [Add-VBRKMSServer](add-vbrkmsserver.md)
* [Get-VBRKMSServer](get-vbrkmsserver.md)
* [Set-VBRKMSServer](set-vbrkmsserver.md)


