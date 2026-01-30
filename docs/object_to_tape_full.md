---
title: "Step 4. Choose Media Pool for Full Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/object_to_tape_full.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Step 4. Choose Media Pool for Full Backup


At the Full Backup step of the wizard, choose a media pool that will be used for archiving full backups of the selected objects and set a schedule for full backups.

1. From the Media pool for full backup list, choose a media pool that will be used for full backups.

You can select a regular media pool or a GFS media pool. Depending on the selected type, the job schedule will change to a regular schedule or GFS schedule.

|  |
| --- |
| Tip |
| If you have not previously created a media pool with the required settings, you can click the Add New button and create a new media pool without closing the job wizard. For more details, see [Creating Media Pools](creating_custom_media_pools.md) or [Creating GFS Media Pools](creating_gfs_media_pools.md). |

1. [For regular media pools] To schedule periodic creation of full backups, select the Run full backup automatically check box and specify the schedule according to which the job will create full backups. If this option is disabled, you will need to start the job manually to create full backups of object storage.

![Step 4. Choose Media Pool for Full Backup](images/object_tape_job_full_backup.webp)


