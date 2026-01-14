---
title: "Step 3. Select Destination"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_failback_destination.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Step 3. Select Destination

In this article

At the Destination step of the wizard, select a failback destination and backup proxies for data transfer during failback:

1. Select a destination for failback. Veeam Backup & Replication supports the following options:

* Failback to the original VM — select this option if you want to fail back to the source VMs that reside on the source hosts. Veeam Backup & Replication will synchronize the state of the source VMs with the current state of their replicas to apply any changes that occurred to the replicas while running in the DR site.

If you select this option, you will proceed to the Failback Mode step of the wizard.

* Failback to the original VM restored in a different location — select this option if the source VMs have already been recovered to a new location, and you want to switch to the recovered VMs from their replicas. Veeam Backup & Replication will synchronize the state of the recovered VMs with the current state of the replicas to apply any changes that occurred to the replicas while running in the DR site.

If you select this option, you will proceed to the Target VM step of the wizard.

* Failback to the specified location — select this option if you want to recover VMs from replicas. You can recover VMs to a new location, or to any location but with different settings (such as network settings, virtual disk type, configuration file path and so on). Select this option if there is no way to fail back to the source VM or an already recovered VM.

If you select this option, the wizard will include additional steps.

If you select one of the first two options, Veeam Backup & Replication will send to the source/recovered VMs only differences between the existing virtual disks. Veeam Backup & Replication will not send replica configuration changes such as different IP address or network settings (if replica Re-IP and network mapping were applied), new hardware or virtual disks added while the replicas were in the Failover state.

If you select Failback to the specified location, Veeam Backup & Replication will send to the specified location whole VM data, including VM configurations and virtual disk content.

1. To select which backup proxies will be used for data transfer, click Pick backup proxies for data transfer. By default, Veeam Backup & Replication selects proxies automatically.

If VMs and their replicas reside in different sites, select at least one backup proxy in the production site and one proxy in the disaster recovery site. If VMs and replicas reside in the same site, you can use the same backup proxy as the source and target one.

We recommend you to select at least two backup proxies in each site to ensure that failback will be performed in case one proxy fails or looses the network connection.

1. [For failback to the original VMs] If you want to fasten failback, and the source VMs had problems at the guest OS level, select the Quick rollback check box. For more information on quick rollback, its requirements and limitations, see [Quick Rollback](cdp_failback_quick_rollback.md).

![Step 3. Select Destination](images/cdp_failback_destination.webp "Select destination")

Page updated 8/21/2025

Page content applies to build 13.0.1.1071
