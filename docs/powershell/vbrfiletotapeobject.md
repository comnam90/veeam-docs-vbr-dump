---
title: "VBRFileToTapeObject"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrfiletotapeobject.html"
last_updated: "12/29/2025"
product_version: "13.0.1.1071"
---

# VBRFileToTapeObject

In this article

Contains file system objects processed by file to tape job.

Properties

| Property | Type | Description |
| --- | --- | --- |
| IncludeMask | string | The mask for selecting files from a directory. |
| ExcludeMask | string | The mask for excluding files from a directory. |
| Path | string | The file or directory path. |
| SelectionObjectType | enum | Indicates the source data type: File, Directory, or Host. |
| Server | CHost | The host where the source files reside. |

Related Commands

[New-VBRFileToTapeObject](new-vbrfiletotapeobject.md)

Page updated 12/29/2025

Page content applies to build 13.0.1.1071
