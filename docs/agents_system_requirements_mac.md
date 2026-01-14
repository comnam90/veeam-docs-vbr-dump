---
title: "System Requirements for Mac Computers"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_system_requirements_mac.html"
last_updated: "11/3/2025"
product_version: "13.0.1.1071"
---

# System Requirements for Mac Computers

In this article

A computer that you want to protect with Veeam Agent for Mac must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| Hardware | The protected macOS computer must meet the following hardware requirements:   * CPU: x64 or ARM Apple-branded hardware1. * Memory: 2 GB RAM or more. Memory consumption varies depending on the total amount of backed-up data. * Disk Space: 600 MB free disk space for product installation. * Network: 10 Mbps or faster network connection to a backup target.   1 On a macOS computer with the ARM Apple-branded hardware, the product is running using the Rosetta Translation Environment. |
| OS | Veeam Agent supports the following macOS versions:   * 26 Tahoe * 15 Sequoia * 14 Sonoma * 13 Ventura * 12 Monterey * 11 Big Sur |
| File System | Veeam Agent supports consistent data backup with snapshot for the APFS file system.  The following file systems can be backed up in the snapshot-less mode:   * HFS+ * MS-DOS (FAT) * exFAT * NTFS * FAT32 * SMB   Consider the following:   * Sortware RAID is not supported. * Total size of all file systems included in a backup must not exceed 216 TiB. * Size of a file in a backup must not exceed 16 TiB. * Name of a file in a backup must not be larger than 254 bytes.   Keep in mind that characters that you can use in the file name may be encoded in 2 bytes or more. |

Page updated 11/3/2025

Page content applies to build 13.0.1.1071
