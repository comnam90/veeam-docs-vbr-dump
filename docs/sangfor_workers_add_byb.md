---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_workers_add_byb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you add a worker to the backup infrastructure, consider the following:

* A worker must be deployed on each cluster whose VMs you plan to protect.
* Each worker must be provided with sufficient compute resources to handle backup and restore tasks in parallel. The maximum number of concurrent tasks is configured in worker settings — if this number is exceeded, the worker will not start a new task until one of the current tasks finishes.
* You can change the maximum number of concurrent tasks (the best practice is to allocate 1 vCPU and 1 GB RAM for each additional task) while deploying a new worker or editing settings of an existing one.

Page updated 2026-07-28

