---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_workers_add_byb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you add a worker to the backup infrastructure, consider the following:

* At least one worker must be deployed in each universal hypervisor environment. It is recommended that workers are deployed on each node of clusters. If no worker is deployed on the node, performance of backup and restore operations will be affected since Veeam Backup & Replication will use a worker deployed on another node.

* Each worker must be provided with sufficient compute resources to handle backup and restore tasks in parallel. The maximum number of concurrent tasks is configured in worker settings — if this number is exceeded, the worker will not start a new task until one of the current tasks finishes.
* You can change the maximum number of concurrent tasks (the best practice is to allocate 1 vCPU and 1 GB RAM for each additional task) while deploying a new worker or editing settings of an existing one.

Page updated 2026-07-10

