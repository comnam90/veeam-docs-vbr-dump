---
title: "FIPS Compliance"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/fips_compliance.html"
last_updated: "1/9/2026"
product_version: "13.0.1.1071"
---

# FIPS Compliance

In this article

Veeam Backup & Replication can be configured to run in a FIPS-compliant operation mode.

When this mode is enabled:

* Veeam Backup & Replication uses [platform-provided cryptographic APIs](communications_encryption.md#encryption_libraries) and the [Veeam Cryptographic Module](https://csrc.nist.gov/projects/cryptographic-module-validation-program/certificate/4282).
* NTLM is disabled. Kerberos is the only available domain authentication protocol.
* Connections cannot be established with components that are not FIPS-compliant.
* Self-tests are performed. For more information, see the Self-tests section of the [Veeam FIPS 140-2 Security Policy](https://csrc.nist.gov/CSRC/media/projects/cryptographic-module-validation-program/documents/security-policies/140sp4282.pdf).

|  |
| --- |
| Note |
| To make your backup infrastructure FIPS-compliant, follow vendor recommendations. For more information on Microsoft Windows Server, see [this article](https://docs.microsoft.com/en-us/windows/security/threat-protection/fips-140-validation#using-windows-in-a-fips-140-2-approved-mode-of-operation). |

To enable the FIPS-compliant operation mode:

1. From the main menu on the backup server, select Options.
2. Open the Security tab.
3. In the FIPS compliance section, select the Force strict FIPS compliance mode check box.
4. Click OK.

|  |
| --- |
| Note |
| If you use Amazon S3 or Amazon S3 Glacier object repositories in your backup infrastructure and enable the FIPS-compliant operation mode, Veeam Backup & Replication checks if these components are FIPS-compliant. If any of them are not, a warning will be displayed. |

|  |
| --- |
| Important |
| If you have backup infrastructure components based on Linux servers with persistent [Veeam Data Movers](veeam_transport_service.md) and select or clear the Force strict FIPS compliance mode check box, you must [open the Edit Linux Server wizard](edit_server.md) for each Linux server with the persistent Veeam Data Mover and proceed to the end of the wizard. This will update server settings. If you do not update the settings, the servers will be unavailable. |

![FIPS Compliance](images/fips_compliance.webp)

Page updated 1/9/2026

Page content applies to build 13.0.1.1071
