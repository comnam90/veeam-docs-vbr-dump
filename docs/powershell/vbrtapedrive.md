---
title: "VBRTapeDrive"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtapedrive.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRTapeDrive

In this article

Contains tape library drive.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Address | int | Number of slot where the drive is connected. |
| Device | string | Tape library to which the drive belongs. |
| Enabled | bool | Indicates if the drive is enabled (TRUE) or not (FALSE). |
| IsLocked | bool | Indicates if the drive is locked by read/write operations (TRUE) or not (FALSE). |
| LibraryId | GUID | The ID of the tape library to which the drive belongs. |
| Medium | [VBRTapeMedium](vbrtapemedium.md) | The name of the tape currently located in the drive. |
| Model | string | The drive model name. |
| SerialNumber | string | The drive serial number. |
| State | [VBRTapeDriveState](enums.md#VBRTapeDriveState) | Drive state. |
| Id | GUID | The drive ID. |
| Name | string | The drive name. |
| Description | string | The drive description. |

Related Commands

[Tape Drives](tape_drives.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
