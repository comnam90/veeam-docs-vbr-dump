---
title: "Manual Start of Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/scheduling_manual_hv.html"
last_updated: "2/12/2025"
product_version: "13.0.1.1071"
---

# Manual Start of Backup Jobs


You can start jobs manually if you need to capture VM data at a specific point in time and do not want to re-configure job scheduling settings. For example, you can start a job to create a VM backup before you install new software on a VM or enable a new feature.

When you start the job manually, Veeam Backup & Replication runs a regular job session that produces a new restore point in the backup chain in the backup repository.

To start and stop jobs configured on the backup server, you can use the Start and Stop buttons on the ribbon or the commands in the shortcut menu.

[![Click to zoom in](images/job_manual_launch.webp)](images/job_manual_launch.webp "Click to zoom in")

Related Topics

[Starting and Stopping Jobs](jobs_start_stop_hv.md)


