---
title: "Managing Workers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_workers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Workers


To perform most data protection and disaster recovery operations (such as creating image-level backups and restoring backed-up data from them), Veeam Backup & Replication uses workers. Workers are Linux-based VMs that process backup workload and distribute backup traffic when transferring data to backup repositories.

Each worker is launched on a specific host for the duration of a backup or restore operation. While configuring the worker, you can manually select the host or instruct Veeam Backup & Replication to choose a host automatically. Manual selection may be helpful if you want to avoid launching workers on specific hosts (for example, production ones), while automatic selection allows Veeam Backup & Replication to optimize data transfer and to balance the load on the hosts in the Nutanix AHV cluster. In the latter case, Veeam Backup & Replication uses the [AHV affinity functionality](https://portal.nutanix.com/page/documents/details?targetId=AHV-Admin-Guide-v10_3:ahv-affinity-policies.html) to distribute workers among all hosts in the cluster instead of launching multiple workers on one host.

Worker Lifecycle

When you add a worker to the backup infrastructure, its configuration is saved to the Veeam Backup & Replication configuration database, but no VM is actually deployed on the host unless you choose to test the configuration. In the latter case, a VM (worker VM) is deployed and shut down after the test operation completes.

As soon as a backup or restore session starts, Veeam Backup & Replication tries to launch the worker and test its configuration. If no worker VM has been previously deployed, Veeam Backup & Replication deploys the VM using the worker configuration saved to the configuration database. Veeam Backup & Replication checks host affinity settings specified for the worker and chooses a host where the worker VM will run. Then, Veeam Backup & Replication powers on the worker VM and installs system updates (if available). When the backup or restore session completes, Veeam Backup & Replication shuts down the worker VM so that it can be used for other sessions later.

During the lifecycle, a worker can obtain one of the following statuses:

Worker Lifecycle

| Icon | Status |
| ![Managing Workers](images/proxmox_worker_configured.webp) | Worker configuration is added to the Veeam Backup & Replication configuration database or worker configuration is being tested |
| ![Managing Workers](images/proxmox_worker_working.webp) | Worker is processing a backup or restore operation |
| ![Managing Workers](images/proxmox_worker_turnedoff.webp) | Worker is powered off |
| ![Managing Workers](images/proxmox_worker_disable.webp) | Worker is disabled |

In This Section

* [Managing Workers Using Console](ahv_worker_console.md)
* [Managing Workers Using Web UI](ahv_workers_web.md)

Page updated 2026-06-24

