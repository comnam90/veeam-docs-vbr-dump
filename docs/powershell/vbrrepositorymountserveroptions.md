---
title: "VBRRepositoryMountServerOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrrepositorymountserveroptions.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRRepositoryMountServerOptions


Contains settings of a mount server for object storage repositories.

Properties

| Property | Type | Description |
| --- | --- | --- |
| MountServer | CHost | Mount server. |
| MountPort | Int32 | Mount server port. |
| MountFolder | String | A folder to keep cache created during mount operations. |
| VPowerNFSPort | Int32 | Network ports used by the Veeam vPower NFS Service. |
| EnableVPowerNFS | Boolean | Enables the Veeam vPower NFS Service on the mount server. |


