---
title: "Instant File Share Recovery"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/instant_nas_recovery.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

Instant file share recovery allows you to recover data from backups of the following file shares:

* SMB file shares

For SMB file shares, you can mount a recovered file share, make changes to the file share (add, edit or remove files and folders), and migrate the file share to the production environment.

* NFS file shares

For NFS file shares, you can use the feature to publish a point-in-time file share state as a read-only SMB file share. This lets you instantly access all recovered files.

After you have performed instant file share recovery, you have to finalize it. For more information, see [Finalizing Instant File Share Recovery](instant_nas_recovery_finalize.md).

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
