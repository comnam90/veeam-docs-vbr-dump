---
title: "Resource Scheduling"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/resource_scheduling.html"
last_updated: "5/9/2025"
product_version: "13.0.1.1071"
---

# Resource Scheduling


Veeam Backup & Replication has the built-in mechanism of resource scheduling. Resource scheduling lets Veeam Backup & Replication automatically define what backup infrastructure resources are required for data protection and disaster recovery jobs and tasks, select optimal resources and assign them for the jobs and tasks.

Resource scheduling is performed by the Veeam Backup Service running on the backup server. When a job or task starts, it communicates with the service and informs it about the resources it needs. The service analyzes job settings, parameters specified for backup infrastructure components, current load on the components, and automatically allocates optimal resources to the job.

For resource scheduling, Veeam Backup Service uses the following settings and features:

* [Limitation of Concurrent Tasks](limiting_tasks.md)
* [Limitation of Read and Write Data Rates for Backup Repositories](limiting_ingestion.md)
* [Performance Bottlenecks](detecting_bottlenecks.md)

Related Topics

[Managing Network Traffic](managing_network_traffic.md)


