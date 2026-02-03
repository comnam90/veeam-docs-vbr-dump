---
title: "Sizing Guidelines"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_sizing_guide.html"
last_updated: "1/12/2026"
product_version: "13.0.1.1071"
---

# Sizing Guidelines


This section is intended for professionals who search for a best practice answer to sizing-related issues, and assumes you have already read the whole Veeam Plug-in for Nutanix AHV User Guide.

Be aware that a best practice is not the only answer available. It will fit in the majority of cases but can also be totally wrong under different circumstances. Make sure you understand the implications of the recommended practices, or request assistance. If in doubt, reach out to Veeam professionals on [Veeam R&D Forums](https://forums.veeam.com).

Workers

While adding a worker to the backup infrastructure, consider the following:

* It is recommended that workers are deployed in each Nutanix AHV cluster. If no worker is deployed in the cluster, performance of backup operations will be affected as Veeam Backup & Replication will use a worker deployed in another cluster.
* It is recommended that the number of configured workers does not exceed the number of hosts in the Nutanix AHV cluster.
* Each worker must be provided with sufficient compute resources to handle backup and restore tasks in parallel. The maximum number of concurrent tasks is configured in worker settings — if this number is exceeded, the worker will not start a new task until one of the current tasks finishes.
* It is recommended the total number of concurrent tasks configured for all workers deployed in the cluster does not exceed the [number of physical disks added to the cluster](https://portal.nutanix.com/page/documents/details?targetId=Web-Console-Guide-Prism-v7_3:wc-hardware-dashboard-wc-r.html). You can change the maximum number of concurrent tasks (the best practice is to allocate 1 vCPU and 1 GB RAM for each additional task) while deploying a new worker or editing settings of an existing one.

|  |
| --- |
| Important |
| To modify the worker settings, use the Veeam Backup & Replication console as described in section [Disabling Automatic Worker Updates](ahv_workers_update.md). Allocating resources to the VM running as a worker in the Nutanix Prism console may cause technical issues. |


