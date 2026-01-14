---
title: "Limitations for Archive Tier"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/limitations_archive_tier.html"
last_updated: "8/13/2025"
product_version: "13.0.1.1071"
---

# Limitations for Archive Tier

In this article

The archive tier has the following limitations:

* If you transfer data to the archive tier from an object storage repository, the archive tier configuration depends on the object storage provider. For more information, see the [Direct Data Transfer to Archive Tier](archive_tier.md#directtoarchive) section.
* Veeam Backup & Replication does not support direct data transfer from performance extents that consist of [Google Cloud Object Storage](adding_google_cloud_object_storage.md) to archive extents.

* Migrating data to another archive tier is not supported.
* Imported backups cannot be offloaded to archive tier.
* Incremental backup files cannot be stored in the archive tier.
* Microsoft Azure Archive Storage with the archive access tier does not support Azure accounts with the following redundancy options: zone-redundant storage (ZRS), geo-redundant storage (GZRS) and read-access geo-zone-redundant storage (RA-GZRS). For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview#archive-access-tier).

Page updated 8/13/2025

Page content applies to build 13.0.1.1071
