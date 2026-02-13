---
title: "Editing Workers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_workers_edit.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Editing Workers


For each worker, you can modify settings specified while adding the worker to the backup infrastructure:

1. Open the Backup Infrastructure view.
2. In the inventory pane, select Backup Proxies.
3. In the working area, select the necessary worker and click Edit Worker on the ribbon.

Alternatively, right-click the worker and select Properties.

1. Complete the Edit Scale Computing HyperCore Worker wizard as described in section [Adding Workers](sch_workers_add.md).

|  |
| --- |
| Important |
| It is not recommended that you decrease the amount of allocated resources or modify the network settings while the worker is currently transferring data. In this case, Veeam Plug-in for Scale Computing HyperCore will terminate the related operations, power off the worker and update the settings immediately. |

[![Editing Workers](images/sch_workers_edit.webp)](images/sch_workers_edit.webp "Editing Workers")


