---
title: "Rescan of Storage Systems"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/netapp_limitations_rescan.html"
last_updated: "5/20/2025"
product_version: "13.0.1.1071"
---

# Rescan of Storage Systems


cDot

| Storage Type | FlexClone (recommended) | SnapRestore | No license (Traditional LUN cloning) |
| --- | --- | --- | --- |
| Primary Storage System | | | |
| iSCSI/FC | Possible | Possible | Not possible |
| NFS | Possible (not used) | Possible | Possible |
| Secondary Storage System: SnapMirror and SnapVault | | | |
| iSCSI/FC | Possible | Not possible | Not possible |
| NFS | Possible | Possible | Possible |

|  |
| --- |
| Note |
| During storage rescan, Veeam Backup & Replication adds its export rules for the storage. New rules are added at the beginning of the list, shifting existing rules down in the list. |


