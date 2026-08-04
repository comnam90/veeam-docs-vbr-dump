---
title: "Testing Workers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_workers_test_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Testing Workers


Before using a dedicated worker for a backup or restore operation, Veeam Backup & Replication automatically tests its configuration — verifies that the worker service can start successfully, checks that the worker can connect to the backup server and to the cluster, and installs available updates.

If you want to ensure that the worker configuration is correct before it is used for a backup or restore operation, you can start a worker configuration test manually:

1. Navigate to Proxies & Workers.
2. Select the worker and click Test Worker.

Note that you can select and test multiple workers at once.

As soon as Veeam Backup & Replication finishes the worker configuration test, the worker will be powered off.

[![Testing Workers](images/pve_workers_test_web.webp)](images/pve_workers_test_web.webp "Testing Workers")

Page updated 2026-07-15

