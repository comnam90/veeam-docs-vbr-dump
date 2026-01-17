---
title: "TLS Certificate"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/ssl_encryption.html"
last_updated: "12/15/2025"
product_version: "13.0.1.1071"
---


In this article

The Veeam Backup Enterprise Manager REST API is a self-hosted Windows Communication Foundation (WCF) service. You can connect to the REST API using either the HTTP or HTTPS protocol. When using HTTPS, the connection between the client and the server is secured with the TLS protocol. In this case, the client verifies the REST API identity with a server TLS certificate.

The REST API certificate is configured during Enterprise Manager installation:

* If you install Enterprise Manager on Linux, a self-signed certificate is generated.
* If you install Enterprise Manager on Microsoft Windows, you can select an existing certificate or generate a new self-signed certificate.

If the existing TLS certificate expires or you want to replace it (for example, with a certificate issued by a Certificate Authority), you can update the current certificate in the Enterprise Manager web UI. For details, see the [Installing Certificates](https://helpcenter.veeam.com/docs/vbr/em/updating_security_certificate.html?ver=13) section of the Veeam Backup Enterprise Manager User Guide.

Page updated 12/15/2025

Page content applies to build 13.0.1.1071
