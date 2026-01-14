---
title: "VBRTapeMedium"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtapemedium.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRTapeMedium

In this article

Contains tape.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| Barcode | string | The tape barcode. |
| BlockSize | int | Specifies the size of the block used for writing data to tapes (in bytes). |
| Capacity | int64 | The tape capacity (in bytes). |
| CleaningCyclesLeft | int? | The number of cleaning cycles left for the cleaning tape. |
| Description | string | The tape description. |
| ExpirationDate | DateTime? | The tape expiration date. Tape expires when all backup sets written to it expires. |
| Free | int64 | The tape free capacity (in bytes). |
| HasBarcode | bool | Indicates if the tape has barcode. |
| Id | GUID | The tape ID. |
| IsExpired | bool | Indicates if the tape is expired and can be rewritten. |
| IsFree | bool | Indicates if the tape is marked as free. |
| IsFull | bool | Indicates if the tape is full. |
| IsLocked | bool | Indicates if the tape is locked in drive, for example, by a tape job. |
| IsRetired | bool | Indicates if the tape is retired: tapes are retired when they achieve maximum rewrite time or has mechanical breakdowns. |
| LastWriteTime | DateTime? | The date and time of last write session. |
| LibraryId | GUID | The ID of the tape library to which the tape belongs. |
| Location | VBRTapeMediumLocation | The tape current location:   * ID and address of drive * ID and address of library slot * ID of vault |
| MediaPoolId | GUID | The ID of the media pool to which the tape belongs. |
| MediaSet | [VBRTapeMediaSet](vbrtapemediaset.md) | The media set to which the tape belongs. |
| Name | string | The tape name. |
| PreviousLibraryId | GUID? | The ID of the library to which the tape belonged previously. |
| PreviousMediaPoolId | GUID? | The ID of the library to which the tape belonged previously. |
| ProtectedByHardware | bool | Indicates if the tape is hardware protected. |
| ProtectedBySoftware | bool | Indicates if the tape is software protected. |
| ReadCyclesNumber | int? | The number of read cycles performed for the tape. |
| SequenceNumber | int? | The sequence number of the tape in media set. |
| WriteCyclesNumber | int? | The number of write cycles performed for the tape. |

Related Commands

[Tapes](tapes.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
