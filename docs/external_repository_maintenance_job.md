---
title: "Maintenance Job"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/external_repository_maintenance_job.html"
last_updated: "8/8/2024"
product_version: "13.0.1.1071"
---

# Maintenance Job

In this article

The maintenance job is a system job that is executed automatically every 24 hours.

The maintenance job does the following:

* Purges obsolete restore points that fall under the retention policy.

To be able to purge obsolete restore points from external repositories due to the retention policy threshold, a Veeam Backup & Replication client must be the owner of a repository and its backup files.

* Purges cache by 20% of the size limit. By default, the size limit is 10GB.
* Saves its session results to the configuration database.

The session results can be found in the History view under the System node.

Related Topics

* [Rescanning External Repositories](rescaning_external_repositories.md)

* [Ownership](external_repository_ownership.md)
* [Managing Retention Policy](external_repository_retention.md)
* [Cache](external_repository_cache.md)

Page updated 8/8/2024

Page content applies to build 13.0.1.1071
