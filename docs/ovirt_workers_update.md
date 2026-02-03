---
title: "Disabling Automatic Worker Updates"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_workers_update.html"
last_updated: "1/19/2026"
product_version: "13.0.1.1071"
---

# Disabling Automatic Worker Updates


When launching a worker for a backup or restore operation, Veeam Backup & Replication automatically downloads updates from Veeam repositories and installs them on the worker. If the worker is not connected to the Internet, you can instruct Veeam Backup & Replication to use an HTTP proxy that will provide access to the necessary repositories.

If a worker does not have access to the internet and no internet proxy is configured for the worker, you can disable automatic updates to avoid connection failures and eliminate session warnings:

1. Open the Backup Infrastructure view.
2. In the inventory pane, select Backup Proxies.
3. In the working area, select the necessary worker and click Edit Worker on the ribbon.

Alternatively, right-click the worker and select Properties.

![Disabling Automatic Worker Updates](images/ovirt_workers_update.webp "Workers Update")


