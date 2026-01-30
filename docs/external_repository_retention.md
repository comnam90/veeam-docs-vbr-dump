---
title: "Managing Retention Policy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/external_repository_retention.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Managing Retention Policy


A retention policy is set in the backup policy settings of [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10), [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\* and [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1) and defines the number of restore points to keep in repositories.

Retention policies are initially managed by Veeam Backup for AWS, Veeam Backup for Google Cloud\* or Veeam Backup for Microsoft Azure until a Veeam Backup & Replication client reclaims ownership of a repository and all the backup files in such a repository.

Once ownership is reclaimed, Veeam Backup for AWS, Veeam Backup for Google Cloud\* or Veeam Backup for Microsoft Azure ceases to govern retention policies and the Veeam Backup & Replication client becomes responsible for removing obsolete restore points from repositories.

The restore points that fall under the retention policy will be removed upon the next successful session of the maintenance job.

When a Veeam Backup & Replication client removes an external repository from its scope, it relinquishes its ownership which then goes directly to Veeam Backup for AWS, Veeam Backup for Google Cloud\* or Veeam Backup for Microsoft Azure until another Veeam Backup & Replication client reclaims it anew and so forth.

|  |
| --- |
| Important |
| A retention policy can only be applied by the Veeam Backup & Replication client that is the rightful owner of an Amazon S3 object storage repository and its backup files. |

\*This feature is available for Microsoft Windows-based backup servers.

Related Topics

* [Maintenance Job](external_repository_maintenance_job.md)

* [Ownership](external_repository_ownership.md)


