---
title: "VBRGlobalNotificationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrglobalnotificationoptions.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# VBRGlobalNotificationOptions

In this article

Contains global notification settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| StorageSpaceThresholdEnabled | bool | Indicates that when the disk space in the target backup repository is below a specific value Veeam Backup & Replication will (TRUE) or will not (FALSE) display a warning. |
| StorageSpaceThreshold | int | Disk space threshold for backup repositories in percent. |
| DatastoreSpaceThresholdEnabled | bool | Indicates that when the disk space in a production datastore is below a specific value Veeam Backup & Replication will (TRUE) or will not (FALSE) display a warning. |
| DatastoreSpaceThreshold | int | Disk space threshold for production datastore in percent. |
| SkipVMSpaceThresholdEnabled | bool | Indicates that when free disk space in this datastore is below the specified threshold Veeam Backup & Replication will stop (TRUE) or will not stop (FALSE) backup jobs that work with production datastores before VM snapshots are taken. |
| SkipVMSpaceThreshold | int | Disk space threshold for production datastore in percent. |
| NotifyOnSupportExpiration | bool | Indicates that Veeam Backup & Replication will (TRUE) or will not (FALSE) notify about the support expiration date in every email notification. |
| NotifyOnUpdates | bool | Indicates that Veeam Backup & Replication will (TRUE) or will not (FALSE) notify about new product versions and patches available on the Veeam website. |

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
