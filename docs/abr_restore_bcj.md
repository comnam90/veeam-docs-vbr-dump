---
title: "Performing Application Backup Repository Restore from Backup Copy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/abr_restore_bcj.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Application Backup Repository Restore from Backup Copy


You can recover the application backup repository data backed up by the backup copy job from the secondary backup repository. This scenario allows you to restore the application backup repository data to any alternative application backup repository host, for example, if the original repository is lost. Veeam Backup & Replication will export the application backup repository data to a temporary NFS share for browsing and selective restore.

Before you perform application backup repository recovery, check [considerations and limitations](abr_limitations.md). Then use the Application Backup Repository Restore wizard.

1. [Launch the Application Backup Repository Restore wizard](abr_bcj_recovery_launch.md).
2. [Select a restore point](abr_bcj_recovery_restore_point.md).
3. [Specify a destination for repository data](abr_bcj_recovery_destination.md).
4. [Specify access permissions](abr_bcj_recovery_permissions.md).
5. [Specify a restore reason](abr_bcj_recovery_reason.md).
6. [Review settings](abr_bcj_recovery_summary.md).
7. [Finalize Application Backup Repository Restore](abr_bcj_recovery_finalize.md).

Page updated 2026-07-10

