---
title: "Veeam Backup Catalog"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/indexing_catalog.html"
last_updated: "2/22/2024"
product_version: "13.0.1.1071"
---

# Veeam Backup Catalog

In this article

For VM guest OS file indexing, Veeam Backup & Replication uses the Veeam Guest Catalog Service. In the backup infrastructure, the Veeam Guest Catalog Service is installed on the Veeam backup server and Veeam Backup Enterprise Manager server.

* The Veeam Guest Catalog Service on the Veeam backup server works as a local catalog service. It collects indexing data for backup jobs and stores it in the Veeam Backup Catalog folder.

By default, the indexing data is stored in the VBRCatalog folder on the backup server. Veeam Backup & Replication creates the folder on a volume with the maximum amount of free space, for example, C:\VBRCatalog.

* The Veeam Guest Catalog Service on Veeam Backup Enterprise Manager works as a global, federal catalog service. It communicates with Veeam Guest Catalog Services on backup servers connected to Veeam Backup Enterprise Manager and performs the following tasks:

+ Replicates indexing data from backup servers to create a global catalog for the whole backup infrastructure.

On the Veeam Backup Enterprise Manager server, the default folder for storing indexing data (the VBRCatalog folder) is located on a volume with the maximum amount of free space.

* Maintains indexing data retention.
* Allows you to search for VM guest OS files in current and archived backup files.

Page updated 2/22/2024

Page content applies to build 13.0.1.1071
