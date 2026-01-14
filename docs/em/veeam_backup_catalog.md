---
title: "veeam_backup_catalog"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/veeam_backup_catalog.html"
last_updated: "7/18/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup Catalog is a feature that stands for VM guest OS file indexing. Veeam Backup Catalog comprises Veeam Guest Catalog services that run on a backup server and Enterprise Manager server.

* Veeam Guest Catalog service on backup server works as a local catalog service. It collects index data for backup jobs on this specific backup server and stores data locally in the Veeam Backup Catalog folder.
* Veeam Guest Catalog service on the Enterprise Manager server works as a federal catalog service. It communicates with Veeam Guest Catalog services on backup servers connected to Enterprise Manager and performs the following tasks:

* Replicates index data from Veeam backup servers to create a federal catalog
* Maintains index data retention
* Lets you search backups for guest OS files

|  |
| --- |
| Note |
| If Veeam Backup & Replication and Veeam Backup Enterprise Manager are installed on the same machine, Veeam Backup Catalog works as a federal catalog service. This makes it impossible to replicate index data from this catalog to another Enterprise Manager. If you want to connect the backup server to another Enterprise Manager, uninstall Enterprise Manager from the current machine first. |

Page updated 7/18/2025

Page content applies to build 13.0.1.1071
