---
title: "Limitations for Archive Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/limitations_archive_tier.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Limitations for Archive Tier


The archive tier has the following limitations:

* If you transfer data to the archive tier from an object storage repository, the archive tier configuration depends on the object storage provider. For more information, see the [Direct Data Transfer to Archive Tier](archive_tier.md#directtoarchive) section.
* Veeam Backup & Replication does not support direct data transfer from performance extents that consist of [Google Cloud Object Storage](adding_google_cloud_object_storage.md) to archive extents.

* Migrating data to another archive tier is not supported.
* Imported backups cannot be offloaded to archive tier.
* Incremental backup files cannot be stored in the archive tier.
* Veeam Backup & Replication supports the copy archive policy only for direct data transfer from the performance tier to the archive tier. If you archive data from the capacity tier, only the move policy is supported.
* Microsoft Azure Archive Storage with thearchive access tier does not support Azure accounts with the following redundancy options: zone-redundant storage (ZRS), geo-redundant storage (GZRS) and read-access geo-zone-redundant storage (RA-GZRS). For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview#archive-access-tier).
* If you specify several gateway servers for Veeam Data Cloud Vault Archive, Veeam Backup & Replication will not distribute data transfer tasks between them equally. All tasks within a session use a single, randomly selected gateway server.

Page updated 2026-07-29

