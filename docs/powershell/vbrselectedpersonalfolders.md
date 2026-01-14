---
title: "VBRSelectedPersonalFolders"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrselectedpersonalfolders.html"
last_updated: "7/25/2024"
product_version: "13.0.1.1071"
---

# VBRSelectedPersonalFolders

In this article

Contains scope of personal data for Agent Backup jobs that back up Microsoft Windows and Mac computers.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| Desktop | bool | Desktop folder |
| Documents | bool | Documents folder |
| Pictures | bool | Pictures folder |
| Video | bool | * Video folder — for Microsoft Windows computers * Movies folder — for Mac computers |
| Favorites | bool | Favorites folder |
| Downloads | bool | Downloads folder |
| ApplicationData | bool | Application data |
| Custom | bool | Custom locations |
| Library | bool | Library folder |
| ExcludeRoamingUsers | bool | Roaming user profiles |
| ExcludeOneDrive | bool | OneDrive folder |

Related Commands

* [New-VBRSelectedFilesBackupOptions](new-vbrselectedfilesbackupoptions.md)
* [Set-VBRSelectedFilesBackupOptions](set-vbrselectedfilesbackupoptions.md)
* [New-VBRSelectedPersonalFolders](new-vbrselectedpersonalfolders.md)
* [Set-VBRSelectedPersonalFolders](set-vbrselectedpersonalfolders.md)

Page updated 7/25/2024

Page content applies to build 13.0.1.1071
