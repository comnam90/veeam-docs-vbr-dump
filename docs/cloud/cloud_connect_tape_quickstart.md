---
title: "Getting Started with Tenant Backup to Tape"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_tape_quickstart.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

To back up tenant data to tape, the SP must complete the following steps:

1. Configure the Veeam Cloud Connect Backup infrastructure. For details, see [Getting Started with Veeam Cloud Connect Backup](cloud_connect_backup_getting_started.md).
2. Connect tape devices and add a tape server to the backup infrastructure on the SP backup server. For details, see [Connecting Tape Devices](https://helpcenter.veeam.com/docs/vbr/userguide/connecting_tape_devices.html?ver=13) and [Adding Tape Servers](https://helpcenter.veeam.com/docs/vbr/userguide/adding_tape_server.html?ver=13) sections in the Veeam Backup & Replication User Guide.
3. Create one or more GFS media pools that will be used as targets for tenant backup to tape jobs. For details, see the [Creating GFS Media Pools](https://helpcenter.veeam.com/docs/vbr/userguide/creating_gfs_media_pools.html?ver=13) section in the Veeam Backup & Replication User Guide.
4. Configure and run a tenant backup to tape job. For details, see [Creating Tenant Backup to Tape Job](cc_backup_to_tape_backup.md).
5. In case some tenant data in a cloud repository becomes missing or corrupted, you can restore the necessary data from tape. For details, see [Restoring Tenant Data from Tape](cc_backup_to_tape_restore.md).

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
