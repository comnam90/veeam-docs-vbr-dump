---
title: "Immutability for Backup Files"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/immutability.html"
last_updated: "12/11/2024"
product_version: "13.0.1.1071"
---

# Immutability for Backup Files

In this article

Veeam Backup & Replication allows you to prohibit the deletion of data from backup repositories by making that data temporarily immutable. It is done to increase security: immutability protects your data against loss due to attacks, malware activity or any other harmful actions.

|  |
| --- |
| Note |
| After you enable immutability, Veeam Backup & Replication will not support the deletion of immutable backups until the immutability expiration date comes. |

You can enable the immutability feature for the following types of backup repositories:

* Dell Data Domain. For more information, see [Immutability for Dell Data Domain](dell_dd.md#immutability).
* Hardened repository. For more information, see [Hardened Repository](hardened_repository.md).
* HPE StoreOnce. For more information, see [HPE StoreOnce Supported Features](storeonce_supported_features.md#immutability).
* Object storage repository. For more information, see [Immutability for Object Storage Repositories](immutability_object_storage_repositories.md).
* Scale-out backup repository. For more information, see [Immutability for Scale-out Backup Repository](immutability_sobr.md).

Page updated 12/11/2024

Page content applies to build 13.0.1.1071
