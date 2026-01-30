---
title: "Importing Certificate from Certificate Store"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/import_tls.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Importing Certificate from Certificate Store


If the Veeam backup server has been issued a TLS certificate signed by a CA and the TLS certificate is located in the Veeam Backup & Replication server certificate store, you can use this certificate for authenticating parties in the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Important |
| If you update the TLS certificate used on the backup server, you must also update info about the certificate on the specific backup infrastructure components as described in section [Backup Server Certificate](backup_server_certificate.md). |

To select a certificate from the certificate store, do the following:

1. From the main menu, select Options.
2. Click the Security tab.
3. In the Security tab, click Install.
4. At the Certificate Type step of the wizard, choose Select certificate from the Certificate Store.

![Importing Certificate from Certificate Store](images/ssl_ca_mode.webp)

1. At the Pick Certificate step of the wizard, select a TLS certificate that you want to use. You can select only certificates that contain both a public key and a private key. Certificates without private keys are not displayed in the list.

![Importing Certificate from Certificate Store](images/ssl_ca_list.webp)

1. At the Summary step of the wizard, review the certificate properties.
2. Click Finish to apply the certificate.


