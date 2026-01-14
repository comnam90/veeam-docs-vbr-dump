---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_disk_recovery_before_you_begin.html"
last_updated: "4/16/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you perform Instant Disk Recovery, consider the following:

* Prerequisites for Instant Disk Recovery from storage snapshots are listed in the [Data Recovery from Storage Snapshots](storage_limitations_general.md#vess) section.
* You can restore a virtual disk from a backup that has at least one successfully created restore point.

* If you want to scan disk data for viruses, check the [secure restore requirements and limitations](av_scan_about.md#av_limitations).
* Instant Disk Recovery to VMware Cloud Director is not supported.

* You must have at least 10 GB of free disk space on the datastore where write cache folder is located. This disk space is required to store virtual disk updates for the restored VM.

By default, Veeam Backup & Replication writes virtual disk updates to the IRCache folder on a volume with the maximum amount of free space, for example, C:\ProgramData\Veeam\Backup\IRCache.

Page updated 4/16/2025

Page content applies to build 13.0.1.1071
