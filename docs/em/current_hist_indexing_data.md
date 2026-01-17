---
title: "Current and Historical Indexing Data"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/current_hist_indexing_data.html"
last_updated: "7/18/2025"
product_version: "13.0.1.1071"
---


In this article

Indexing data structures in Veeam Backup Catalog are divided into two groups:

* Current indexing data stores information for valid restore points that are currently available in the backup chain in the backup repository. For example, if the retention policy for a backup job is set to 14, Veeam Backup Catalog will contain indexing data for 14 restore points and 14 backup job sessions.
* Historical indexing data stores information for obsolete restore points: the points that were removed from the backup chain. When you run a backup job to create a new restore point, the earliest restore point is marked as obsolete and removed from the backup chain. Indexing data for this restore point in the Veeam Backup Catalog is not removed. Instead, it is marked as historical.

Historical indexing data helps the user accomplish file search in backup files that were archived to tape or to a secondary backup repository.

By default, Veeam Backup Enterprise Manager keeps historical indexing data for 3 months. To change this value, navigate to the Configuration > Settings > Session History > Guest file system catalog section in Veeam Backup Enterprise Manager.

[![Historical Indexing Data](images/em_catalog_retention_settings.webp)](images/em_catalog_retention_settings.webp "Historical Indexing Data")

Related Topics

[Configuring Retention Settings for Index and History](configuring_retention_settings.md)

Page updated 7/18/2025

Page content applies to build 13.0.1.1071
