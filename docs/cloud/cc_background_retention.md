---
title: "Background Retention for Tenant Backups"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_background_retention.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

In addition to applying a retention policy within a job session, Veeam Backup & Replication performs background retention for backups.

In the Veeam Cloud Connect infrastructure, background retention is applied to tenant backups on the SP side. The background retention job runs automatically in Veeam Backup & Replication on the SP backup server according to the same rules as in the regular Veeam backup infrastructure. The SP can also launch background retention manually. For details, see the [Background Retention](https://helpcenter.veeam.com/docs/vbr/userguide/background_retention_job.html?ver=13) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Note |
| The SP can also disable background retention. |

For background retention of tenant backups in the cloud repository, in addition to considerations for the regular background retention, consider the following:

* To all types of tenant accounts, the same background retention rules are applied.
* Background retention is applied to backups created by tenants and their subtenants.
* The background retention job removes tenant backups regardless of whether the tenant is in the Enabled or Disabled state.
* Insider protection is supported. If the insider protection functionality is enabled for the tenant account, backups removed by the background retention job are moved to the "recycle bin".
* If the SP removes the tenant account and does not delete tenant backup files from the cloud repository, the background retention job will remove the backup files in the same way as a regular orphaned backup chain.

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
