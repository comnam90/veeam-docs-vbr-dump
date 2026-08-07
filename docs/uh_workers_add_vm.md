---
title: "Step 2. Specify Worker VM Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_workers_add_vm.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 2. Specify Worker VM Settings


At the Virtual Machine step of the wizard, do the following:

1. Click Choose next to the Cluster field to specify a cluster where the worker will be launched.
2. In the Name field, specify a name for the worker. The maximum length of the name is 63 characters; only the following characters are supported: a-z, A-Z, 0-9, -.
3. Click Choose next to the Storage field, and specify storage where worker system files will be stored.
4. In the Description field, provide a description for future reference. The maximum length of the description is 1024 characters.
5. In the Max concurrent tasks field, specify the number of tasks that the worker will be able to handle in parallel; the number must be between 2 and 128. If this value is exceeded, the worker will not start processing a new task until one of the currently running tasks finishes.

The default number of concurrent tasks is set to 4. When you change this value, the wizard automatically adjusts the amount of resources that will be allocated to the worker. If you want to specify the amount of resources manually, click Advanced settings.

|  |
| --- |
| Note |
| When performing data protection and disaster recovery operations, Veeam Backup & Replication initiates a new task for each VM that is being processed. |

1. To specify a host where the worker will be launched, click Advanced settings, select the Host affinity check box and choose the host.

If you do not specify host affinity settings, Veeam Backup & Replication will automatically define the host to launch the worker.

|  |
| --- |
| Note |
| Ensure that you do not specify hosts in the disabled state, offline state or switched to the maintenance mode since they are still displayed in the list of available hosts. |

[![Specify Worker VM Settings](images/uh_workers_add_vm.webp)](images/uh_workers_add_vm.webp "Specify Worker VM Settings")

Page updated 2026-07-24

