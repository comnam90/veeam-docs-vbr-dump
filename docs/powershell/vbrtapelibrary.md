---
title: "VBRTapeLibrary"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtapelibrary.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRTapeLibrary


Contains tape library.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Drives | [VBRTapeDrive](vbrtapedrive.md)[] | The tape library drives. |
| Enabled | bool | Indicates if the drives are enabled (TRUE) or not (FALSE). |
| Model | string | The model names of the drives. |
| Slots | int | The number of tape slots in the tape library. |
| TapeServerId | GUID | The ID of the tape server to which the tape library is connected. |
| Type | [VBRTapeLibraryType](enums.md#VBRTapeLibraryType) | Tape library type. |
| State | [VBRTapeLibraryState](enums.md#VBRTapeLibraryState) | Tape library state. |
| Id | GUID | The tape library ID. |
| Name | string | The tape library name. |
| Description | string | The tape library description. |

Related Commands

[Tape Libraries](tape_libraries.md)


