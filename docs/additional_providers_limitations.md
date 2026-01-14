---
title: "Additional Providers Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/additional_providers_limitations.html"
last_updated: "11/21/2025"
product_version: "13.0.1.1071"
---

# Additional Providers Considerations and Limitations

In this article

Limitations for 11:11 Cloud Object Storage

Consider the following limitations:

* You cannot use 11:11 Cloud Object Storage as an archive extent for [Archive Tier](archive_tier.md) of a scale-out backup repository.
* You cannot use 11:11 Cloud Object Storage in the same type of a scale-out backup repository tier (either the performance tier or the capacity tier) with Amazon S3 repository.

Limitations for IBM Cloud Object Storage

Consider the following limitations:

* For IBM Cloud Object Storage on-premises, Veeam Backup & Replication supports versions starting from 3.15.0.44.
* Veeam Backup & Replication is supported on all IBM Cloud Object Storage (COS) deployment models. This includes on-premises, public cloud, and hybrid models. For the IBM public cloud, the following storage classes are supported: Standard, Vault, Cold Vault and Smart Tier.
* Veeam Backup & Replication does not support Archive and Accelerated Archive storage classes in the IBM public cloud.

Limitations for Wasabi Cloud Storage

You cannot add as performance extents one Wasabi bucket as an [S3 compatible Object Storage](adding_s3c_object_storage.md) and another Wasabi bucket as a [Wasabi Cloud Object Storage](adding_wasabi_object_storage.md) to the same type of tier (either performance tier or capacity tier) of a scale-out backup repository.

Page updated 11/21/2025

Page content applies to build 13.0.1.1071
