---
title: "VBRTapeGFSMediaSetPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtapegfsmediasetpolicy.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRTapeGFSMediaSetPolicy

In this article

Contains GFS media set advanced options.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Medium | [VBRTapeMedium](vbrtapemedium.md)[] | Tapes added to this media set. |
| MoveFromMediaPoolAutomatically | bool | Indicates if the media set will be replenished by tapes from the parent media pool (TRUE) or not (FALSE). |
| Name | string | Media set name. |
| AppendToCurrentTape | bool | Indicates if the new data is appended to the tape with previously written data (TRUE) or a new tape is used for each backup set (FALSE). |
| MoveOfflineToVault | bool | Indicates if the offline tapes must be automatically moved to a vault (TRUE) or not (FALSE). |
| Vault | [VBRTapeVault](vbrtapevault.md) | Vault to which the offline tapes are moved. |

Related Commands

[New-VBRTapeMediaSetCreationPolicy](new-vbrtapemediasetcreationpolicy.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
