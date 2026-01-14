---
title: "Cache"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/external_repository_cache.html"
last_updated: "6/14/2024"
product_version: "13.0.1.1071"
---

# Cache

In this article

Veeam Backup & Replication caches data that is being retrieved from external repositories every time a backup copy job or restore session is performed.

Such an approach helps not only to reduce the number of cost-expensive operations incurred by AWS, Microsoft Azure or Google Cloud, but also decrease the amount of traffic being sent over the network.

Consider the following:

* Cache is created on a gateway server while the following activities are being processed:

+ Backup copy jobs.
+ Restore sessions.

* Cache is not created upon the addition of an external repository to the Veeam Backup & Replication console.
* Cache consists of metadata of blocks being retrieved from external repositories.
* Cache is written to:

+ On a Windows-based gateway server: C:\ProgramData\Veeam\ExternalCache
+ On a Linux-based gateway server: /var/veeam/ExternalCache

* Cache is reused and updated during each subsequent execution of a backup copy job or restore session.
* Cache size limit is 10GB. Once reached, Veeam will purge obsolete cache by 20% preserving most frequently used parts. Purging is done by the maintenance job.
* Cache is removed in the following cases:

+ An external repository has been removed from the Veeam Backup & Replication console.
+ The gateway server has been changed in the settings of the external repository configuration.
+ The backup file has been removed from the external repository.
+ During the maintenance job session.

* Cache can be removed manually without affecting the backup infrastructure in any negative way.

Related Topics

[Maintenance Job](external_repository_maintenance_job.md)

Page updated 6/14/2024

Page content applies to build 13.0.1.1071
