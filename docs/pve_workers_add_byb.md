---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_workers_add_byb.html"
last_updated: "6/2/2026"
product_version: "13.0.2.29"
---

# Before You Begin


Before you add a worker to the backup infrastructure, consider the following:

* It is recommended that workers are deployed on each node registered with a Proxmox VE cluster. If no worker is deployed on the node, performance of backup and restore operations will be affected as Veeam Backup & Replication will use a worker deployed on another node.

* Each worker must be provided with sufficient compute resources to handle backup and restore tasks in parallel. The maximum number of concurrent tasks is configured in worker settings — if this number is exceeded, the worker will not start a new task until one of the current tasks finishes.
* You can change the maximum number of concurrent tasks (the best practice is to allocate 1 vCPU and 1 GB RAM for each additional task) while deploying a new worker or editing settings of an existing one.
* Veeam Plug-in for Proxmox VE does not support migration of workers between cluster nodes using the [Proxmox VE HA](https://pve.proxmox.com/wiki/High_Availability).


