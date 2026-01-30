---
title: "Backup from Storage Snapshots"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_from_storage_snapshots_hiw_netapp.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Backup from Storage Snapshots


cDot

| Storage Type | FlexClone (recommended) | SnapRestore | No license (Traditional LUN cloning) |
| --- | --- | --- | --- |
| Primary Storage System | | | |
| iSCSI/FC | Possible | Possible | Not possible |
| NFS | Possible (not used) | Possible (not used) | Possible |
| Secondary Storage System: SnapMirror and SnapVault | | | |
| iSCSI/FC | Possible | Not possible | Not possible |
| NFS | Possible (not used) | Possible (not used) | Possible |

|  |
| --- |
| Note |
| During backup from storage snapshots, Veeam Backup & Replication adds its export rules for the storage. New rules are added at the beginning of the list, shifting existing rules down in the list. |

In This Section

* [Traditional LUN Cloning](storage_backup_netapp_cloning.md)
* [FlexClone](storage_backup_netapp_flexclone.md)
* [SnapRestore](storage_backup_netapp_snaprestore.md)
* [NFS Protocol](storage_backup_netapp_nfs.md)


