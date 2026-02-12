---
title: "Managing Workers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_workers.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Managing Workers


To perform most data protection and disaster recovery operations, Veeam Plug-in for Scale Computing HyperCore uses workers. Workers are Linux-based VMs that process backup workload and distribute backup traffic when transferring data to backup repositories. Each worker is launched on a specific host for the duration of a backup or restore operation.

|  |
| --- |
| Important |
| To modify the worker settings, use the Veeam Backup & Replication console as described in section [Editing Workers](sch_workers_edit.md). Making any configuration changes to VMs running as workers manually in the Scale Computing HyperCore administration portal may cause technical issues. |

Worker Lifecycle

When you add a worker to the backup infrastructure, its configuration is saved to the Veeam Backup & Replication configuration database, but no VM is actually deployed on the host unless you choose to test the configuration. In the latter case, a VM (worker VM) is deployed and shut down after the test operation completes.

As soon as a backup or restore session starts, Veeam Plug-in for Scale Computing HyperCore tries to launch the worker and test its configuration. If no worker VM has been previously deployed, Veeam Plug-in for Scale Computing HyperCore deploys the VM using the worker configuration saved to the configuration database. Then, Veeam Plug-in for Scale Computing HyperCore powers on the worker VM and installs system updates (if available). When the backup or restore session completes, Veeam Plug-in for Scale Computing HyperCore shuts down the worker VM so that it can be used for other sessions later.

During the lifecycle, a worker can obtain one of the following statuses:

* Configured — the worker configuration is added to the Veeam Backup & Replication configuration database.
* Testing — the worker configuration is being updated and tested.
* Working — the worker is processing a backup or restore operation.
* Shut Down — the worker is powered off.

In This Section

* [Adding Workers](sch_workers_add.md)
* [Testing Workers](sch_workers_test.md)
* [Enabling and Disabling Workers](sch_workers_disable.md)
* [Editing Workers](sch_workers_edit.md)
* [Disabling Automatic Worker Updates](sch_workers_update.md)
* [Removing Workers](sch_workers_remove.md)


