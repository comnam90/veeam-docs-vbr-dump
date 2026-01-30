---
title: "FlexClone"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_restore_netapp_flexclone.html"
last_updated: "4/16/2025"
product_version: "13.0.1.1071"
---

# FlexClone


For NetApp storage systems that have a FlexClone license installed, Veeam Backup & Replication uses the NetApp FlexClone technology for restore from storage snapshots.

During restore from storage snapshots, Veeam Backup & Replication creates a FlexClone of a LUN. The storage snapshot from which you want to restore data is used as a base copy. The FlexClone is then mounted to an ESXi host, and you can restore the necessary VM data from it.

![FlexClone](images/netapp_restore_flexclone.webp)


