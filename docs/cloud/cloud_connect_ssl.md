---
title: "TLS Certificates"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_ssl.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

Communication between components in the Veeam Cloud Connect infrastructure is carried out over a TLS connection secured with a TLS certificate. The TLS certificate is used for verification of trust. It helps the SP and tenants identify themselves and make sure that parties taking part in data transfer are really the ones that they claim to be.

Veeam Backup & Replication does not use TLS certificates to encrypt data traffic in the Veeam Cloud Connect infrastructure. For data encryption, Veeam Backup & Replication uses the same encryption methods and algorithms as in a regular backup infrastructure.

In This Section

* [Types of TLS Certificates](cloud_connect_ssl_types.md)
* [TLS Certificates Handshake](cloud_connect_ssl_handshake.md)
* [TLS Certificate Thumbprint Verification](cloud_connect_ssl_verify.md)
* [Rights and Permissions to Access TLS Certificates](cloud_connect_ssl_rights.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
