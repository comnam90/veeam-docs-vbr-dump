---
title: "VBRTapeGFSMediaPool"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtapegfsmediapool.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRTapeGFSMediaPool


Contains GFS media pool.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Name | string | The media pool name. |
| Description | string | The media pool description. |
| LibraryId | GUID | The ID of the first tape library in the array of libraries managed by the media pool. |
| MoveFromFreePool | bool | Indicates that the media pool will be replenished by tapes from the Free media pool automatically (TRUE) or not (FALSE). |
| WeeklyMediaSetOptions | [VBRTapeGFSMediaSetOptions](vbrtapegfsmediasetoptions.md) | The advanced settings of weekly media set. |
| MonthlyMediaSetOptions | [VBRTapeGFSMediaSetOptions](vbrtapegfsmediasetoptions.md) | The advanced settings of monthly media set. |
| QuarterlyMediaSetOptions | [VBRTapeGFSMediaSetOptions](vbrtapegfsmediasetoptions.md) | The advanced settings of quarterly media set. |
| YearlyMediaSetOptions | [VBRTapeGFSMediaSetOptions](vbrtapegfsmediasetoptions.md) | The advanced settings of yearly media set. |
| EncryptionOptions | [VBREncryptionOptions](vbrencryptionoptions.md) | The data encryption options applied to the media pool. |
| GlobalOptions | [VBRGlobalMediaPoolOptions](vbrglobalmediapooloptions.md) | The global media pool options. |

Related Commands

* [Add-VBRTapeGFSMediaPool](add-vbrtapegfsmediapool.md)
* [Set-VBRTapeGFSMediaPool](set-vbrtapegfsmediapool.md)
* [Remove-VBRTapeMediaPool](remove-vbrtapemediapool.md)


