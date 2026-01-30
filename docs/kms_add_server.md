---
title: "Adding KMS Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/kms_add_server.html"
last_updated: "5/15/2025"
product_version: "13.0.1.1071"
---

# Adding KMS Server


To add a KMS server, do the following:

1. From the main menu, select Credentials and Passwords > Key Management Servers.
2. In the Key Management Servers window, click Add.
3. In the Server field, specify the FQDN, IPv4 or IPv6 address of the server. By default, the port number 5696 is used.
4. In the Server certificate field, click Browse and specify a KMS server certificate. You can select one of the following options:

1. Select an existing certificate from the certificate store. You can specify a KMS server certificate if it is located in the Microsoft Windows certificate store.
2. Import certificate from a file. You can import a KMS server certificate from a file in the PFX, CER, or PEM format.

|  |
| --- |
| Note |
| If you use a server certificate in the PEM format, it must contain the -----BEGIN CERTIFICATE----- header at the beginning of the file and the -----END CERTIFICATE----- footer at the end of the file. |

For more information about requirements that a server certificate must meet, see [KMS Certificates](kms_certificates.md).

![Adding KMS Server](images/kms_add_server_certificate.webp)

1. In the Client certificate field, click Browse and specify the client certificate issued by the KMS administrator for Veeam Backup & Replication. You can select one of the following options:

1. Select an existing certificate from the certificate store. You can specify a client certificate issued by the KMS administrator for Veeam Backup & Replication if it is located in the Microsoft Windows certificate store.
2. Import certificate from a file. You can import a client certificate from a file in the PFX format.

|  |
| --- |
| Note |
| If you use a PEM-encoded file, select the Import certificate from a PEM file option. |

1. Import certificate from a PEM file. You can import a client certificate from a PEM-encoded file. Consider the following:

* You must have two separate PEM files for the certificate and private key.

* The certificate must contain the -----BEGIN CERTIFICATE----- header at the beginning of the file and the -----END CERTIFICATE----- footer at the end of the file.
* The private key must be in the PKCS#1 format. Also, it must contain the -----BEGIN RSA PRIVATE KEY----- header at the beginning of the file and the -----END RSA PRIVATE KEY----- footer at the end of the file.

For more information about requirements that a client certificate must meet, see [KMS Certificates](kms_certificates.md).

![Adding KMS Server](images/kms_add_client_certificate.webp)

1. [Optional] In the Description field, provide the description for future reference.
2. Click OK.

![Adding KMS Server](images/kms_add_server.webp)


