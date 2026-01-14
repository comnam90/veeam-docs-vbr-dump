---
title: "indexing_data_retention"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/indexing_data_retention.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

The retention policy for Veeam Backup Catalog helps you maintain the necessary amount of indexing data on the Veeam Backup Enterprise Manager server.

The retention policy for Veeam Backup Catalog is controlled by two values:

* Retention policy for a backup job on the Veeam backup server: the number of restore points in the backup chain
* Retention period for indexing data in Veeam Backup Enterprise Manager

The retention period is calculated differently for backup chains created with different backup methods:

* [Retention for forward incremental backup chains](forward_increment_retention.md)
* [Retention for reverse incremental backup chains](reversed_incremental_retention.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
