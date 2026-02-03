---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_workers_add_byb.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you add a worker to the backup infrastructure, consider the following:

* It is recommended that workers are deployed in each cluster. If no worker is deployed in the cluster, performance of backup operations will be affected as Veeam Backup & Replication will use a worker deployed in another cluster.
* It is recommended that the number of configured workers does not exceed the number of hosts in the cluster.

* Each worker must be provided with sufficient compute resources to handle backup and restore tasks in parallel. The maximum number of concurrent tasks is configured in worker settings — if this number is exceeded, the worker will not start a new task until one of the current tasks finishes.
* You can change the maximum number of concurrent tasks (the best practice is to allocate 1 vCPU and 1 GB RAM for each additional task) while deploying a new worker or editing settings of an existing one.

* It is recommended the total number of concurrent tasks configured for all workers deployed in the cluster does not exceed the [number of physical disks added to the cluster](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_3:wc-hardware-dashboard-wc-r.html).


