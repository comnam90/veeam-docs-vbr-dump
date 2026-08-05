---
title: "Overview"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/overview.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Overview


Veeam Plug-in for Kasten is a solution that allows you to create and manage data protection and disaster recovery tasks for Veeam Kasten environments. Veeam Plug-in for Kasten extends the Veeam Backup & Replication functionality and provides access to Veeam Plug-in for Kasten in the Veeam Backup & Replication console.

|  |
| --- |
| Note |
| Veeam Plug-in for Kasten is built on top of Veeam Backup & Replication, and this guide assumes that you have a good understanding of the Veeam Backup & Replication and Veeam Kasten solutions. |

With Veeam Plug-in for Kasten, you can perform the following operations in the Veeam Backup & Replication console:

* Add a Veeam Kasten instance to the Veeam Backup & Replication infrastructure, manage and remove it.

* Manage Veeam Kasten policies from the Veeam Backup & Replication infrastructure.

* View Veeam Kasten backups exported by the Veeam Kasten policies.

* Restore from Veeam Kasten backups.
* Restore from Veeam Kasten snapshots.
* Monitor session statistics.

If you export Veeam Kasten backups to the Veeam backup repository, you can also perform the following operations:

* Remove backups exported by Veeam Kasten policies from the Veeam Backup & Replication infrastructure.
* Synthesize an independent full backup file using restore points that are located in your Veeam backup repositories.
* Export disks.
* Perform First Class Disk Recovery.
* Restore guest OS files and folders.
* Export backup files.

|  |
| --- |
| Note |
| If you export Veeam Kasten backups to a location other than a Veeam backup repository, you can view these backups in the Veeam Backup & Replication console. For all other operations you will be navigated to the Veeam Plug-in for Kasten web console. |

Related Resources

* [Backup Infrastructure Components](infrastructure_components.md)
* [Planning and Preparation](planning_and_preparation.md)
* [Deployment and Configuration](deployment.md)
* [Data Protection](data_protection.md)
* [Data Recovery](data_recovery.md)

Page updated 2026-08-04

