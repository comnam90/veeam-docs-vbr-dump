---
title: "forward_increment_retention"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/forward_increment_retention.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

The retention policy for the forward incremental backup chain is calculated by the following formula:

Retention period = MAX (Catalog Retention, X)

where:

* Catalog Retention is the retention period specified in Veeam Backup Enterprise Manager.
* X is the amount of time for which restore points are kept by a backup job.

For example, the retention policy settings are specified in the following manner:

* The retention policy for a backup job is set to 5 points. The backup job is run daily.
* The retention period in Veeam Backup Enterprise Manager is set to 1 month, or 30 days.

In this case, Veeam Backup Enterprise Manager will retain indexing data for 30 days, because this value is greater than the number of restore points in the job.

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
