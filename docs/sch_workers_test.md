---
title: "Testing Workers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_workers_test.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Testing Workers


Before using a dedicated worker for a backup or restore operation, Veeam Plug-in for Scale Computing HyperCore automatically tests its configuration — verifies that the worker service can start successfully, checks that the worker can connect to the backup server and to the host, and installs available updates.

If you want to ensure that the worker configuration is correct before it is used for a backup or restore operation, you can start a worker configuration test manually:

1. Open the Backup Infrastructure view.
2. In the inventory pane, select Backup Proxies.
3. In the working area, select the necessary worker and click Test Worker on the ribbon.

Alternatively, right-click the worker and select Test.

|  |
| --- |
| Tip |
| As soon as Veeam Plug-in for Scale Computing HyperCore finishes the worker configuration test, the worker will be powered off. You can review details of the test session in system logs as described in the Veeam Backup & Replication User Guide, section [Viewing History Statistics](history_statistics.md). |

[![Testing Workers](images/sch_workers_test.webp)](images/sch_workers_test.webp "Testing Workers")


