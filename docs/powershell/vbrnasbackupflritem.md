---
title: "VBRNASBackupFLRItem"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrnasbackupflritem.html"
last_updated: "1/17/2024"
product_version: "13.0.1.1071"
---

# VBRNASBackupFLRItem

In this article

Contains settings of restored guest OS files and folders that have been backed up by file backup jobs.

Properties

| Property | Type | Description |
| --- | --- | --- |
| CreationDate | DateTime | Date and time of creation. |
| Path | String | Path to the file on a file share. |
| Name | String | Name of the file. |
| Parent | VBRNASBackupFLRFolder | Parent folder. |
| ModificationDate | DateTime | Date and time of last modification. |
| VersionId | UInt64 | Version of the file. |

Related Commands

[Save-VBRNASBackupFLRItem](save-vbrnasbackupflritem.md)

Page updated 1/17/2024

Page content applies to build 13.0.1.1071
