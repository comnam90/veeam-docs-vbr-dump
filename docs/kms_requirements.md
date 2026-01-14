---
title: "Requirements and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/kms_requirements.html"
last_updated: "10/8/2025"
product_version: "13.0.1.1071"
---

# Requirements and Limitations

In this article

The KMS feature has the following requirements and limitations:

* The feature is included in the Veeam Data Platform Advanced or Premium License. For more details about all license types, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf). Data decryption is available for all licenses.
* To configure KMS servers and use KMS keys, a desktop version of the Veeam Backup & Replication console is required. The feature is not supported in the web UI.
* Veeam Backup & Replication supports KMS servers that meet the following requirements:

* Key Management Interoperability Protocol (KMIP) Profile v1.4. Other versions of KMIP Profiles are not supported by Veeam Backup & Replication.
* Requirements for a baseline server. For more information, see the [Baseline Server](https://docs.oasis-open.org/kmip/profiles/v1.4/os/kmip-profiles-v1.4-os.html#_Toc491431430) section in the KMIP Profile standard.
* Requirements for an asymmetric key lifecycle server. For more information, see the [Asymmetric Key Lifecycle Server](https://docs.oasis-open.org/kmip/profiles/v1.4/os/kmip-profiles-v1.4-os.html#_Toc491431516) section in the KMIP Profile standard.

|  |
| --- |
| Tip |
| The list of tested KMS solutions includes the following vendor product lines:   * Thales CipherTrust Manager k170v 2.10.0+7973 and later * Fortanix Data Security Manager KMS 4.20.2274 and later (Public Cloud solution) * IBM Security Guardium Key Lifecycle Manager (GKLM) 4.1.1.0 and later |

* To decrypt data, the KMS server must support:

+ Requirements for a basic cryptographic server. For more information, see the [Basic Cryptographic Server](https://docs.oasis-open.org/kmip/profiles/v1.4/os/kmip-profiles-v1.4-os.html#_Toc491431527) section in the KMIP Profile standard.
+ Optimal Asymmetric Encryption Padding (OAEP) with SHA-1.

In other cases, Veeam Backup & Replication will retrieve private keys from the KMS server to decrypt backup files. These keys are not stored in the configuration database and deleted immediately after decryption.

* [For Cloud Connect] To use the KMS feature in the Veeam Cloud Connect environment, both a service provider and a tenant must run Veeam Backup & Replication 12.1 (build 12.1.0.2131) or later.
* [For Cloud Connect] If a tenant uses the same KMS server as a service provider, backup files stored in the tenant quota cannot be decrypted on the service provider side.

Page updated 10/8/2025

Page content applies to build 13.0.1.1071
