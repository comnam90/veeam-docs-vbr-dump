---
title: "Failback on VSAN"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/failback_vsan.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Failback on VSAN

In this article

Due to specifics of VSAN data storage organization, Veeam Backup & Replication cannot get the difference between disks of a VM replica located on VSAN and disks of the source VM in a regular manner. Veeam Backup & Replication needs to read VM disks data anew in every failback process phase. As a result, failback for VMs replicas on VSAN slightly differs from the regular failback course.

Before Veeam Backup & Replication starts the failback process, it checks the location of VM replica disks. If at least one disk is located on VSAN, Veeam Backup & Replication performs failback in the following way:

1. Veeam Backup & Replication creates a working failback snapshot for the source VM.
2. For every VM disk, Veeam Backup & Replication performs the following actions:

1. If you fail back to the source VM location, Veeam Backup & Replication calculates the difference between the VM replica disk and the source VM disk. To do this, Veeam Backup & Replication reads the whole amount of disk data from VSAN, and transfers only changed data to the source VM side.
2. If you fail back to a new location, Veeam Backup & Replication transfers the whole disk without calculating the difference.

1. The VM replica is powered off.
2. Veeam Backup & Replication creates a protective failback snapshot for the VM replica. Using the protective failback snapshot, Veeam Backup & Replication detects what changes took place on the VM replica while VM disk data was being transported. As well as before, Veeam Backup & Replication reads the whole amount of VM disks data but transports only those data blocks that have changed since the VM disks transfer.

The rest of the failback process does not differ from the regular failback process.

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
