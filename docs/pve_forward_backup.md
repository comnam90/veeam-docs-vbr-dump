---
title: "Forward Incremental Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_forward_backup.html"
last_updated: "1/21/2026"
product_version: "13.0.1.1071"
---

# Forward Incremental Backup


To create a backup chain for a VM protected by a backup job with scheduled full backups, Veeam Backup & Replication implements the forward incremental backup method:

1. During the first (full) backup session, Veeam Backup & Replication copies the full VM image and creates a full backup file in the backup repository. The full backup file becomes a starting point in the backup chain.
2. During subsequent backup sessions, Veeam Backup & Replication copies only those data blocks that have changed since the previous backup session, and stores these data blocks to incremental backup files in the backup repository. The content of each incremental backup file depends on the content of the full backup file and the preceding incremental backup files in the backup chain.

![Forward Incremental Backup](images/vplugins_backup_chain.webp)

1. On a day when the synthetic full or active full backup is scheduled, Veeam Backup & Replication creates a full backup file and adds it to the backup chain. Incremental restore points produced after this full backup file use it as a new starting point.

![Forward Incremental Backup](images/vplugins_forward_incremental_chain.webp)


