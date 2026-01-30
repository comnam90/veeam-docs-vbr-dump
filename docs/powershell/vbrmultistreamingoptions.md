---
title: "VBRMultiStreamingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmultistreamingoptions.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRMultiStreamingOptions


Contains media pool multistreaming options.

Properties

| Property | Type | Description |
| --- | --- | --- |
| EnableMultiStreaming | bool | Indicates if multistreaming is enabled. |
| NumberOfStreams | int | The maximum number of drives that can be used by the media pool simultaneously. |
| SplitJobFilesBetweenDrives | bool | Indicates if the tape job data will be written with miltiple drives. |

Related Objects

[VBRTapeMediaPool](vbrtapemediapool.md)


