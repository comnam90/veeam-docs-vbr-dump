---
title: "KMS Certificates"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/kms_certificates.html"
last_updated: "5/21/2024"
product_version: "13.0.1.1071"
---

# KMS Certificates

In this article

The KMS server certificate must meet the following requirements:

* The Subject extension must be equal to the fully qualified domain name (FQDN) of the KMS server. For example: kms.domain.local.
* The server certificate must have valid CRL distribution points specified in the CRL Distribution Points extension.
* If the Veeam Backup & Replication server does not trust the Certificate Authority (CA) of the server certificate, it should be added to the Trusted Root Certification Authority store.

The client certificate issued by the KMS administrator for Veeam Backup & Replication must be exportable.

Page updated 5/21/2024

Page content applies to build 13.0.1.1071
