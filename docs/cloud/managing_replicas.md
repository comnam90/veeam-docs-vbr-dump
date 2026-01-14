---
title: "managing_replicas"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/managing_replicas.html"
last_updated: "1/30/2024"
product_version: "13.0.1.1071"
---


In this article

The tenant can perform the following operations with VM replicas created with replication jobs and CDP policies targeted at the cloud host:

* [View properties](view_replica_properties.md)
* [Delete from disk](delete_backup_from_disk_2.md)

|  |
| --- |
| Note |
| The tenant cannot perform the Remove from configuration operation with VM replicas on the cloud host. Such VM replicas are actually stored on the remote DR site in the SP virtualization environment. As a result, they could become permanently inaccessible for a tenant. The tenant may also be unable to delete replica files from the cloud host.  The Remove from configuration operation is available only for the SP in the SP Veeam Backup & Replication console. To learn more, see [Removing from Configuration](cloud_connect_remove_replica_sp.md). |

Page updated 1/30/2024

Page content applies to build 13.0.1.1071
