---
title: "overview"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/overview.html"
last_updated: "12/16/2024"
product_version: "13.0.1.1071"
---


In this article

Veeam Plug-In for Kasten is a solution that allows you to create and manage data protection and disaster recovery tasks for Veeam Kasten environments. Veeam Plug-In for Kasten extends the Veeam Backup & Replication functionality and provides access to Veeam Plug-In for Kasten in Veeam Backup & Replication console.

|  |
| --- |
| Note |
| Veeam Plug-In for Kasten is built on top of Veeam Backup & Replication, and this guide assumes that you have a good understanding of the Veeam Backup & Replication solution and Veeam Kasten solutions. |

With Veeam Plug-In for Kasten, you can perform the following operations in Veeam Backup & Replication console:

* Add the Veeam Kasten instance to Veeam Backup & Replication infrastructure, manage and remove it.

* Manage Veeam Kasten policies from Veeam Backup & Replication infrastructure.

* View Veeam Kasten backups exported by Veeam Kasten policies.

* Restore from Veeam Kasten backups.
* Restore from Veeam Kasten snapshots.
* Monitor session statistics.

If you export Veeam Kasten backups to the Veeam backup repository, you can also perform the following operations:

* Remove backups exported by Veeam Kasten policies from the Veeam Backup & Replication infrastructure.
* Synthesize an independent full backup file using restore points that are located in your Veeam backup repositories.
* Export disks.
* Perform First Class Disk Recovery.
* Restore guest OS files and folders of backups.
* Export backup files.

|  |
| --- |
| Note |
| If you export Veeam Kasten backups to other than the Veeam backup repository, you will be able to view these backups in the Veeam Backup & Replication console. For all other operations you will be navigated to the Veeam Plug-In for Kasten web console. |

Related Resources

* [Backup Infrastructure Components](infrastructure_components.md)
* [Planning and Preparation](planning_and_preparation.md)
* [Deployment and Configuration](deployment.md)
* [Data Protection](data_protection.md)
* [Data Recovery](data_recovery.md)

Page updated 12/16/2024

Page content applies to build 13.0.1.1071
