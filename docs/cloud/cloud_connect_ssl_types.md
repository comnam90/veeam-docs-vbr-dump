---
title: "Types of TLS Certificates"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_ssl_types.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---

# Types of TLS Certificates


Veeam Backup & Replication can work with the following types of TLS certificates:

* TLS certificate verified by a Certificate Authority (CA). If the SP already has a TLS certificate verified by a CA, the SP can import this TLS certificate and use it to establish a secure connection between Veeam Cloud Connect infrastructure components.
* Self-signed certificates. If the SP does not have a TLS certificate verified by a CA, the SP can generate a self-signed TLS certificate with Veeam Backup & Replication. For TLS certificate generation, Veeam Backup & Replication employs the RSA Full cryptographic service provider by Microsoft Windows installed on the Veeam backup server.

The SP can also generate a self-signed certificate with any third-party solution and import it to Veeam Backup & Replication.

|  |
| --- |
| Note |
| Consider the following:   * For communication between the SP and tenants, Veeam Backup & Replication uses a separate TLS certificate from a certificate used for connection between the Veeam backup server and backup infrastructure components. [Requirements for the Veeam backup server certificate](https://helpcenter.veeam.com/docs/vbr/userguide/backup_server_certificate.html?ver=13) do not apply to certificates in the Veeam Cloud Connect infrastructure. The SP can use a certificate issued by a third-party CA and intended for usage on a web server. * For more information on how to sign a certificate that the SP plans to use in the Veeam Cloud Connect infrastructure, see [this web page](https://vccbook.io/8.advanced/8.1-ssl_certificates.html). |


