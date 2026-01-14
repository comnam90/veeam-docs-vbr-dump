---
title: "VBRGlobalMediaPoolOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrglobalmediapooloptions.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRGlobalMediaPoolOptions

In this article

Contains tape library failover settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| NextLibOffline | bool | Indicates that the media pool must switch to the next managed library in case the primary library is offline. |
| NestLibDrivesBusy | bool | Indicates that the media pool must switch to the next managed library in case the primary library has no available drives. |
| NextLibNoMedia | bool | Indicates that the media pool must switch to the next managed library in case the primary library has no available tapes. |
| LibraryId | GUID[] | The array of tape library IDs managed by this media pool. |

Related Objects

* [VBRTapeGFSMediaPool](vbrtapegfsmediapool.md)
* [VBRTapeMediaPool](vbrtapemediapool.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
