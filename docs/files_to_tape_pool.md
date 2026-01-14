---
title: "Step 4. Choose Media Pool for Full Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/files_to_tape_pool.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Step 4. Choose Media Pool for Full Backup

In this article

At the Full Backup step of the wizard, choose a media pool that will be used for archiving full backups of the selected files and create a schedule for full file backups.

1. From the Media pool for full backups list, choose a media pool that will be used for full file backups.

You can select a regular media pool or a GFS media pool. Depending on the selected type, the job schedule will change to a regular schedule or GFS schedule.

|  |
| --- |
| Tip |
| If you have not previously created a media pool with the required settings, you can click the Add New button and create a new media pool without closing the job wizard. For more details, see [Creating Media Pools](creating_custom_media_pools.md) or [Creating GFS Media Pools](creating_gfs_media_pools.md). |

1. [For regular media pools] To schedule periodic creation of full file backups, select the Run full backup automatically check box and specify the schedule according to which the job will create full file backups. If this option is disabled, you will need to start the job manually to create full backups of files.

![Step 4. Choose Media Pool for Full Backup](images/files_to_tape_pool.webp)

Page updated 7/7/2025

Page content applies to build 13.0.1.1071
