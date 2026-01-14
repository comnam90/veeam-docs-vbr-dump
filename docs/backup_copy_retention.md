---
title: "Retention Policy for Backup Copy Jobs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_retention.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Retention Policy for Backup Copy Jobs

In this article

The retention policy of a backup copy job defines for how long Veeam Backup & Replication must retain copied restore points in the target backup repository. The retention policy of a backup copy job does not depend on retention policy of the source backup job. The backup copy job has its own retention policy settings.

Veeam Backup & Replication offers two retention policy schemes for backup copy jobs:

* [Short-Term Retention Policy](backup_copy_simple_retention.md)
* [GFS Retention Policy (Weekly, Monthly, Yearly)](backup_copy_gfs.md)

Also, there is a separate retention policy for machines that has been removed from the infrastructure. For details, see [Deleted Items Retention](backup_copy_deleted_vms.md).

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
