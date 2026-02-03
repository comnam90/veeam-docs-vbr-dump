---
title: "Disabling Automatic Worker Updates"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_workers_update.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Disabling Automatic Worker Updates


When launching a worker for a backup or restore operation, Veeam Backup & Replication automatically downloads updates from Veeam repositories and installs them on the worker. If the worker is not connected to the internet, you can instruct Veeam Backup & Replication to [use an internet proxy](pve_workers_add_network.md) that will provide access to the necessary repositories.

If a worker does not have access to the internet and no internet proxy is configured for the worker, you can disable automatic updates to avoid connection failures and eliminate session warnings:

1. Open the Backup Infrastructure view.
2. In the inventory pane, select Backup Proxies.
3. In the working area, select the necessary worker and click Edit Worker on the ribbon.

Alternatively, right-click the worker and select Properties.

1. At the Networks step of the Edit Proxmox VE Worker wizard, click Advanced and clear the Check for updates online check box. Then, click Finish to save changes made to the worker settings.

[![Updating Workers](images/pve_workers_update.webp)](images/pve_workers_update.webp "Updating Workers")

Related Topics

[Ports](pve_used_ports.md)


