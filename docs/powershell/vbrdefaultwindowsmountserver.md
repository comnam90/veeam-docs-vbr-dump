---
title: "VBRDefaultWindowsMountServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrdefaultwindowsmountserver.html"
last_updated: "7/18/2025"
product_version: "13.0.1.1071"
---

# VBRDefaultWindowsMountServer


Contains default Windows mount server and its settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| MountServer | CHost | Mount server. |
| EnableVPowerNFS | Boolean | Enables the Veeam vPower NFS Service on the mount server. |
| VPowerNFSPort | Int32 | Network port used by the Veeam vPower NFS Service. |
| MountPort | Int32 | Mount server port. |
| MountFolder | String | A folder to keep cache created during mount operations. |

Related Commands

* [Set-VBRDefaultWindowsMountServer](set-vbrdefaultwindowsmountserver.md)
* [Get-VBRDefaultWindowsMountServer](get-vbrdefaultwindowsmountserver.md)


