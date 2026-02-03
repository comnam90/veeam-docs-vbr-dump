---
title: "Publishing Disks"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_disk_publish.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Publishing Disks


Veeam Backup & Replication allows you to mount specific disks of backed-up VMs to any server and to instantly access data in the read-only mode. This can be helpful when you want to copy files and folders as of a point-in-time state to the target server, and perform an antivirus scan of the backed-up data. For more information, see [Disk Publishing (Data Integration API)](data_integration_api.md).

To publish VM disks, do the following:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, expand the necessary backup job, right-click the VM that contains disks you want to mount and select Publish disks.

Alternatively, expand the necessary backup job, select the VM and click Publish disks on the ribbon.

1. Complete the Publish Disk wizard as described in section [Publishing Disks](publishing_disks.md).

[![Publishing disks](images/pve_disk_publish.webp)](images/pve_disk_publish.webp "Publishing disks")


