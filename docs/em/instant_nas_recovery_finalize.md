---
title: "Finalizing Instant File Share Recovery"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/instant_nas_recovery_finalize.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Finalizing Instant File Share Recovery


After you have performed instant file share recovery, you have to finalize the process. You can migrate recovered file shares to the production environment or stop publishing.

* [For NFS file shares] When you perform instant recovery of an NFS file share, the file share is published as a read-only SMB file share that lets you instantly access all recovered files. After you finish working with the files, you must stop publishing the recovered file share.
* [For SMB file shares] When you perform instant recovery of an SMB file share, the published file share is available for reading and writing. After you finish working with the files, you must stop publishing the recovered file share or migrate it to the production environment.

Until you finalize instant recovery of all recovered file shares, a notification about running instant recovery sessions is displayed on the Dashboard tab.


