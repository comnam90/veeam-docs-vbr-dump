---
title: "Managing TLS Certificates"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_manage_ssl.html"
last_updated: "6/19/2024"
product_version: "13.0.1.1071"
---

# Managing TLS Certificates


The procedure of TLS certificate creation and management is performed by the SP on the SP Veeam backup server.

When you deploy the Veeam Cloud Connect infrastructure, you must first specify what TLS certificate must be used to establish a secure connection between parties. Veeam Backup & Replication offers the following options for TLS certificates:

* You can use Veeam Backup & Replication to generate a self-signed TLS certificate. To learn more, see [Generating Self-Signed Certificates](cloud_connect_self_signed_ssl.md).
* You can select an existing TLS certificate from the certificates store. To learn more, see [Importing Certificates from Certificate Store](cloud_connect_import_ssl.md).
* You can import a TLS certificate from a file in the PFX format. To learn more, see [Importing Certificates from Files](cloud_connect_import_ssl_pfx.md).

|  |
| --- |
| Note |
| After you specify TLS certificate settings in the Veeam Cloud Connect infrastructure, when you launch the Manage Certificate wizard once again, Veeam Backup & Replication also offers an option to keep the currently used certificate. To do this, select the Keep the existing certificate option at the Certificate Type step of the wizard.  You can use this option to check information about the currently installed certificate, such as name, expiration date, thumbprint and serial number. |

Related Concepts

[TLS Certificates](cloud_connect_ssl.md)


