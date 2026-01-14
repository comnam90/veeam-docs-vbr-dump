---
title: "Communications Encryption Standards"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/communications_encryption_standards.html"
last_updated: "12/22/2025"
product_version: "13.0.1.1071"
---

# Communications Encryption Standards

In this article

To encrypt communication, Veeam Backup & Replication supports the following libraries, modules, and algorithms:

* SHA-256 — for digital signature generation and SSH fingerprint verification.
* SHA-1 — for HMAC generation, backward compatibility, and certificate thumbprint generation.
* OpenSSL, cryptographic libraries provided by the operating system — for random number generation.
* [Veeam Cryptographic Module](https://csrc.nist.gov/projects/cryptographic-module-validation-program/certificate/4872) — for Linux-based components and services. This module is also used for [Veeam Data Mover](veeam_transport_service.md) installed on Microsoft Windows-based machines.
* Microsoft Crypto API — for other Microsoft Windows-based components and services.

* Microsoft Base Cryptographic Provider. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/windows/desktop/SecCrypto/microsoft-base-cryptographic-provider).
* Microsoft Enhanced RSA and AES Cryptographic Provider. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/windows/desktop/SecCrypto/microsoft-aes-cryptographic-provider).
* Microsoft Enhanced Cryptographic Provider. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/windows/desktop/SecCrypto/microsoft-enhanced-cryptographic-provider).

|  |
| --- |
| Note |
| If you need Veeam Cryptographic Module and Microsoft Crypto API to be compliant with the Federal Information Processing Standards (FIPS 140), enable FIPS compliance as described in section [FIPS Compliance](fips_compliance.md). |

Certificates stored in the configuration database are encrypted with specific data protection mechanisms. For more information, see [How Database Data Encryption Works](encryption_database_hiw.md).

Page updated 12/22/2025

Page content applies to build 13.0.1.1071
