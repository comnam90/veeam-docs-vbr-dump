---
title: "performing_permanent_failover"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/performing_permanent_failover.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---


In this article

To finalize the full site failover process, you can perform permanent failover. With permanent failover, you can permanently switch from the original VM to a VM replica and use the VM replica on the cloud host as the original VM.

To perform permanent failover, do either of the following:

* Open the Home view, in the inventory pane select Replicas. In the working area, select the necessary VM and click Permanent Failover on the ribbon.
* Open the Home view, in the inventory pane select Replicas. In the working area, right-click the necessary VM and select Permanent failover.

In the displayed window, click Yes to confirm the operation.

After the permanent failover operation completes, the VM replica is put to the Permanent failover state. To protect the VM replica from corruption after performing permanent failover, Veeam Backup & Replication reconfigures the replication job and adds the original VM to the list of exclusions. When the replication job that processes the original VM starts, the VM will be skipped from processing, and no data will be written to the working VM replica.

[![Perform Permanent Failover](images/permanent_failover.webp)](images/permanent_failover.webp "Perform Permanent Failover")

Page updated 4/17/2024

Page content applies to build 13.0.1.1071
