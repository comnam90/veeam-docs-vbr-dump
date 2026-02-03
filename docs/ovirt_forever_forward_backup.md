---
title: "Forever Forward Incremental Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_forever_forward_backup.html"
last_updated: "1/21/2026"
product_version: "13.0.1.1071"
---

# Forever Forward Incremental Backup


To create a backup chain for a VM protected by a backup job without a full backup schedule, Veeam Backup & Replication implements the forever forward incremental backup:

1. During the first (full) backup session, Veeam Backup & Replication copies the full VM image and creates a full backup file in the backup repository. The full backup file becomes a starting point in the backup chain.
2. During subsequent backup sessions, Veeam Backup & Replication copies only those data blocks that have changed since the previous backup session, and stores these data blocks to incremental backup files in the backup repository. The content of each incremental backup file depends on the content of the full backup file and the preceding incremental backup files in the backup chain.

![Forever Forward Incremental Backup](images/vplugins_backup_chain.webp)


