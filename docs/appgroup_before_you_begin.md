---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/appgroup_before_you_begin.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create an application group, consider the following:

* The availability of the feature depends on the license you use. For more details about licensing support, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).
* All applications and services on which verified machines are dependent must be virtualized in your environment.
* If you plan to scan machines data for malware, [check requirements and limitations](av_scan_about.md#av_limitations).
* If you plan to verify machines with a ping test, the firewall on tested machine must allow ping requests.
* If you plan to verify machines with a heartbeat test, VMware Tools must be installed in tested machines.

* If backup file that is used to add the machine to an application group cannot be found, Veeam Backup & Replication will search for other backup files containing this machine.

* VM replicas must be in the Ready state. If a VM replica is in the Failover or Failback state, you will not be able to add it to the application group.
* You cannot add to application groups VMs from backups of VMware Cloud Director VMs, backups created with backup copy jobs and backups stored in Cloud Connect backup repositories.

* [For storage snapshots] The storage system must be added to the backup infrastructure.


