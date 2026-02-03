---
title: "Managing Workers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_workers.html"
last_updated: "1/9/2026"
product_version: "13.0.1.1071"
---

# Managing Workers


To perform most data protection and disaster recovery operations, Veeam Backup & Replication uses workers. Workers are Linux-based VMs that process backup workload and distribute backup traffic when transferring data to backup repositories. Each worker is launched on a specific host for the duration of a backup or restore operation. As soon as a backup or restore session starts, Veeam Backup & Replication launches a worker, tests its configuration and installs system updates (if available). When the backup or restore session completes, Veeam Backup & Replication shuts down the worker VM so that it can be used for other sessions later.

|  |
| --- |
| Important |
| To modify the worker settings, use the Veeam Backup & Replication console as described in section [Editing Workers](pve_workers_edit.md). Making any configuration changes to VMs running as workers manually in the Proxmox VE administration portal may cause technical issues. |

Worker Lifecycle

When you add a worker to the backup infrastructure, its configuration is saved to the Veeam Backup & Replication configuration database, but no VM is actually deployed in the cluster unless you choose to test the configuration. In the latter case, a VM (worker VM) is deployed and shut down after the test operation completes.

As soon as a backup or restore session starts, Veeam Backup & Replication tries to launch the worker and test its configuration. If no worker VM has been previously deployed, Veeam Backup & Replication deploys the VM using the worker configuration saved to the configuration database. Veeam Backup & Replication checks host affinity settings specified for the worker and chooses a host where the worker VM will run. Then, Veeam Backup & Replication powers on the worker VM and installs system updates (if available). When the backup or restore session completes, Veeam Backup & Replication shuts down the worker VM so that it can be used for other sessions later.

During the lifecycle, a worker can obtain one of the following statuses:

* Configured — the worker configuration is added to the Veeam Backup & Replication configuration database.
* Testing — the worker configuration is being tested.
* Updating — the worker or its configuration is being updated.
* Working — the worker is processing a backup or restore operation.
* Shut Down — the worker is powered off.

In This Section

* [Adding Workers](pve_workers_add.md)
* [Testing Workers](pve_workers_test.md)
* [Enabling and Disabling Workers](pve_workers_disable.md)
* [Editing Workers](pve_workers_edit.md)
* [Disabling Automatic Worker Updates](pve_workers_update.md)
* [Removing Workers](pve_workers_remove.md)


