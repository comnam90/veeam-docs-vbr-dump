---
title: "Using Certificate Signed by Internal CA"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tls_internal_ca.html"
last_updated: "3/3/2026"
product_version: "13.0.1.1071"
---

# Using Certificate Signed by Internal CA


If you want to use a certificate signed by an internal Certificate Authority (CA), consider the following:

* The Veeam Backup & Replication server must trust the CA:

* For Microsoft Windows-based Veeam Backup & Replication, add the certificate to the Trusted Root Certification Authority store.
* For Linux-based Veeam Backup & Replication, copy the CA certificate to the /etc/pki/ca-trust/source/anchors/ directory in the PEM format, and then run the following command as the root user.

|  |
| --- |
| update-ca-trust extract |

* [For Linux-based Veeam Agent computers] OpenSSL version 1.0 or later must be installed on the Veeam Agent computer.

To start using the signed certificate, you must select it from the certificates store on the Veeam Backup & Replication server. To learn more, see [Importing Certificate from Certificate Store](import_tls.md).

Certificate Requirements

A certificate signed by a CA must meet the following requirements.

Certificate Requirements

| Requirement | Description |
| Subject | Must be set to the fully qualified domain name (FQDN) of the Veeam Backup & Replication server. |
| Subject Alternative Name (SAN) | Must include both the FQDN and the NetBIOS name. You can specify multiple DNS entries in the following format:  DNS:vbrserver.domain.local, DNS:vbrserver |
| Key Size | The minimum key size is 2048 bits. |
| Key Usage Extensions | The following key usage extensions are enabled in the certificate:   * Digital Signature * Certificate Signing * Off-line CRL Signing * CRL Signing (06) |
| Basic Constraints | The Path Length Constraint parameter must be set to 0.  The Subject Type parameter must be set to CA. |
| Key Type | Must be set to Exchange. |

|  |
| --- |
| Important |
| The following certificates are not supported:   * Certificates issued by public CAs * Elliptic Curve Signature (ECC) certificates * Cryptography API: Next Generation (CNG) certificates |

CRL Requirements

Ensure that Certificate Revocation List (CRL) published by a CA and containing revoked certificates is accessible from the Veeam Backup & Replication server to verify certificate status. The CRL must meet the following requirements:

* CRL is accessible from the Veeam Backup & Replication server to verify certificate status.
* CRL must have an HTTP endpoint.
* CRL must be signed with a strong cryptographic algorithm such as RSA-SHA256.

Configuring Certificate Templates in Windows Server CA

If you use Windows Server Certification Authority for managing certificates, perform the following steps to configure a suitable certificate template:

1. Open the Certificate Templates Microsoft Management Console (MMC) snap‑in.
2. Select a template based on the built‑in Subordinate Certification Authority template or a similar template.
3. On the Extensions tab, enable the Make this extension critical and Do not allow subject to issue certificates to other CAs options.
4. Issue an Veeam Backup & Replication certificate based on this template.


