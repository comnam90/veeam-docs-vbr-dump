---
title: "Starting and Stopping SureBackup Job"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_job_start.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Starting and Stopping SureBackup Job

In this article

You can instruct the SureBackup job to verify the latest restore point of a VM backup or VM replica or select a specific restore point to which the VM from the backup or VM replica must be started.

To start a VM from the latest restore point:

1. Open the Home view.
2. In the inventory pane, click SureBackup under Jobs.
3. In the working area, select the SureBackup job and click Start on the ribbon. You can also right-click the SureBackup job and select Start. Veeam Backup & Replication will start, verify and perform necessary tests for VMs from the latest restore point.

To start VMs from a specific point in time:

1. Open the Home view.
2. In the inventory pane, select SureBackup under Jobs.
3. In the working area, select the SureBackup job and click Start to on the ribbon. You can also right-click the SureBackup job and select Start to.
4. In the Restore Point window, select an approximate date of the restore point creation. Veeam Backup & Replication will pick the most recent restore point prior to this time and start, verify and perform necessary tests for VMs from this restore point.
5. If SureBackup job is configured to process VM replicas added to a CDP policy, specify the restore point type:

* Application-consistent. SureBackup job will pick the most recent long-term application-consistent restore point prior to the time you specified.
* Crash-consistent. SureBackup job will pick the most recent long-term crash-consistent restore point prior to the time you specified.

[![Click to zoom in](images/surebackup_start_to.webp)](images/surebackup_start_to.webp "Click to zoom in")

To stop a running SureBackup job session:

1. Open the Home view.
2. In the inventory pane, select SureBackup under Jobs.
3. In the working area, select the SureBackup job and click Stop on the ribbon. You can also right-click the SureBackup job and select Stop.

[![Click to zoom in](images/surebackup_stop.webp)](images/surebackup_stop.webp "Click to zoom in")

Page updated 9/3/2025

Page content applies to build 13.0.1.1071
