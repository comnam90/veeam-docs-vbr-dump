---
title: "Using Certificate Signed by Internal CA"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_tls_internal_ca.html"
last_updated: "12/17/2025"
product_version: "13.0.1.1071"
---


In this article

You can use a certificate signed by an internal Certificate Authority (CA) to secure communication between Enterprise Manager and connected components.

Before installing a certificate signed by an internal CA, you must add the certificate to the certificate store on the Enterprise Manager machine to ensure that Enterprise Manager trusts the CA.

Certificate Requirements

A certificate signed by a CA must meet the following requirements.

| Requirement | Description |
| --- | --- |
| Subject | Must be set to the fully qualified domain name (FQDN) of the Enterprise Manager server. |
| Subject Alternative Name (SAN) | Must include both the FQDN and the NetBIOS name. You can specify multiple DNS entries in the following format:  DNS:emserver.domain.local, DNS:emserver |
| Key Size | The minimum key size is 2048 bits. |
| Key Usage Extensions | The following key usage extensions are enabled in the certificate:   * Digital Signature * Certificate Signing * Off-line CRL Signing * CRL Signing (86) |
| Basic Constraints | The Path Length Constraint parameter must be set to 0. |
| Key Type | Must be set to Exchange. |

|  |
| --- |
| Important |
| The following certificates are not supported:   * Certificates issued by public CAs * Elliptic Curve Signature (ECC) certificates * Cryptography API: Next Generation (CNG) certificates |

CRL Requirements

Ensure that Certificate Revocation List (CRL) published by a CA and containing revoked certificates is accessible from the Enterprise Manager server to verify certificate status. The CRL must meet the following requirements:

* CRL is accessible from the Enterprise Manager server to verify certificate status.
* CRL must have an HTTP endpoint.
* CRL must be signed with a strong cryptographic algorithm such as RSA-SHA256.

Configuring Certificate Templates in Windows Server CA

If you use Windows Server Certification Authority for managing certificates, perform the following steps to configure a suitable certificate template:

1. Open the Certificate Templates Microsoft Management Console (MMC) snap‑in.
2. Select a template based on the built‑in Subordinate Certification Authority template or a similar template.
3. On the Extensions tab, enable the Do not allow subject to issue certificates to other CAs option.
4. Issue an Enterprise Manager certificate based on this template.

Adding Certificate to Certificate Store

If you want to use a certificate signed by an internal CA, ensure that Enterprise Manager trusts the CA. After you add the certificate to the certificate store, you can install the certificate. If you attempt to install a certificate without adding it to the store first, the installation will fail. For details on how to install an Enterprise Manager certificate, see [Installing Certificates](updating_security_certificate.md).

* For Microsoft Windows-based Enterprise Manager, add the certificate to the Trusted Root Certification Authority store.
* For Linux-based Enterprise Manager, copy the CA certificate to the /etc/pki/ca-trust/source/anchors/ directory in the PEM format, and then run the following command as the root user.

|  |
| --- |
| update-ca-trust extract |

Page updated 12/17/2025

Page content applies to build 13.0.1.1071
