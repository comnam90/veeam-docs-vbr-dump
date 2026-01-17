---
title: "Tenant Backup to Tape Job"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_tape_job.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---

# Tenant Backup to Tape Job


To back up tenant data to tape, you must create and run tenant backup to tape jobs. Technically, a tenant backup to tape job is a variant of a backup to tape job targeted at a GFS media pool. For more information about GFS media pools, see the [GFS Media Pools](https://helpcenter.veeam.com/docs/vbr/userguide/gfs_media_pools.html?ver=13) section in the Veeam Backup & Replication User Guide.

As a source for a tenant backup to tape job, you can specify the following types of objects:

* All tenants
* One or more specific tenants
* One or more cloud repositories of the same tenant or different tenants

Backups created by tenant backup to tape jobs become available in the Backups > Tape node of the SP Veeam backup console. Such backups are not displayed in the tenant Veeam backup console.

|  |
| --- |
| Note |
| Consider the following:   * Tenant backup to tape jobs process only backups created by jobs or mapped to jobs configured on tenant backup servers. Imported backups are skipped from processing. * If you use the Capacity Tier functionality to offload tenant data to an object storage repository, keep in mind that backup to tape jobs copy to tape active backup chains only (that is, backup chains that reside in performance tier). Inactive backup chains offloaded to an object storage repository are not processed by backup to tape jobs. To learn more about Capacity Tier support in Veeam Cloud Connect, see [Support for Capacity Tier](cloud_connect_capacity_tier.md). |

Related Tasks

[Creating Tenant Backup to Tape Job](cc_backup_to_tape_backup.md)


