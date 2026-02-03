---
title: "Editing Workers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_workers_edit.html"
last_updated: "1/29/2026"
product_version: "13.0.1.1071"
---

# Editing Workers


For each worker, you can modify settings specified while adding the worker to the backup infrastructure:

1. Open the Backup Infrastructure view.
2. In the inventory pane, select Backup Proxies.
3. In the working area, select the necessary worker and click Edit Worker on the ribbon.

Alternatively, right-click the worker and select Properties.

1. Complete the Edit Nutanix AHV Worker wizard:

1. To provide a new name and description for the worker or to modify the number of tasks that the worker is able to handle in parallel, follow the instructions provided in section [Adding Workers](ahv_workers_add_vm.md) (step 2).
2. To change the network to which the worker is connected or to specify a new IP address for the worker, follow the instructions provided in section [Adding Workers](ahv_workers_add_network.md) (step 3).
3. To save changes made to the worker settings, click Finish.

|  |
| --- |
| Important |
| It is not recommended that you change the worker cluster, decrease the amount of allocated resources, adjust the affinity settings or modify the network settings while the worker is currently transferring data. In this case, Veeam Backup & Replication will terminate the related operations, power off the worker and update the settings immediately. |

[![Editing Workers](images/ahv_workers_edit.webp)](images/ahv_workers_edit.webp "Editing Workers")


