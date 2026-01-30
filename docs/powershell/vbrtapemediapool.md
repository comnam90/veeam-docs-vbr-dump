---
title: "VBRTapeMediaPool"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtapemediapool.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRTapeMediaPool


Contains simple media pool.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Capacity | int64 | Total capacity of tapes that belong to the media pool (in bytes). |
| EncryptionOptions | [VBREncryptionOptions](vbrencryptionoptions.md) | The data encryption options applied to the media pool. |
| FreeSpace | int64 | Total free capacity of tapes that belong to the media pool (in bytes). |
| LibraryId | GUID | The ID of the tape library to which the media pool belongs. |
| MediaSetCreationPolicy | [VBRTapeMediaSetCreationPolicy](vbrtapemediasetcreationpolicy.md) | The media sets creation policy applied to this media pool. |
| MediaSetName | string | The name of media sets cretated in this media pool. |
| Medium | [VBRTapeMedium](vbrtapemedium.md) | The tapes that belong to this media pool. |
| MoveFromFreePool | bool | Indicates if the media pool can be replenished from the Free media pool. |
| MoveOfflineToVault | bool | Indicates if the offline are moved to a vault. |
| RetentionPolicy | [VBRTapeMediaPoolRetentionPolicy](vbrtapemediapoolretentionpolicy.md) | The retention policy applied to the media pool. |
| Vault | [VBRTapeVault](vbrtapevault.md) | The vault to which the offline tapes are moved. |
| Type | [VBRTapeMediaPoolType](enums.md#VBRTapeMediaPoolType) | Media pool type. |
| MultiStreamingOptions | [VBRMultiStreamingOptions](vbrmultistreamingoptions.md) | The tape multistreaming options applied to this media pool. |
| GlobalOptions | [VBRGlobalMediaPoolOptions](vbrglobalmediapooloptions.md) | The global media pool options applied to this media pool. |

Related Commands

* [Add-VBRTapeMediaPool](add-vbrtapemediapool.md)
* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [Remove-VBRTapeMediaPool](remove-vbrtapemediapool.md)
* [Set-VBRTapeMediaPool](set-vbrtapemediapool.md)


