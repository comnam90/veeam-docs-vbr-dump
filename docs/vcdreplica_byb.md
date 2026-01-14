---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcdreplica_byb.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a VMware Cloud Director replication job, check the following prerequisites:

* Check the supported Cloud Director versions in [Supported Platforms, Applications and Workloads](platform_support.md#cloud_dir).

* You must [add VMware Cloud Director server](adding_vcloud_director.md) to the backup infrastructure. The backup server must be able to resolve short names and connect to source and target virtualization hosts.
* You must [set up the organization VDC](https://docs.vmware.com/en/VMware-Cloud-Director/10.4/VMware-Cloud-Director-Service-Provider-Admin-Portal-Guide/GUID-D8A4277E-6F45-45D2-94D0-58D2E1175C67.html) that will keep the replicas.
* You must disable the VM discovery option in VMware Cloud Director settings. For more information on where you can change the option, see [VMware Docs](https://docs.vmware.com/en/VMware-Cloud-Director/10.3/VMware-Cloud-Director-Service-Provider-Admin-Portal-Guide/GUID-068B8D3E-11B4-4B67-A653-B374AFD98303.html#activating-vm-discovery-0).
* Veeam Backup & Replication does not support protection of workloads with 4K native disks (disks with 4096 bytes logical sector size).
* VMware Cloud Director replication does not support replication of a vApp to a Cloud Provider.

|  |
| --- |
| Note |
| It is possible to replicate vSphere VMs to your Cloud Provider Cloud. For more information, see [Creating Replication Jobs](replica_job.md). |

* If you plan to replicate VM containers using WAN accelerators, source and target WAN accelerators must be added to the backup infrastructure and properly configured. For more information, see [Adding WAN Accelerators](wan_add.md).
* If you plan to replicate VM containers using WAN accelerators, it is recommended that you pre-populate global cache on the target WAN accelerator before you start the VMware Cloud Director replication job. Global cache population helps reduce the amount of traffic transferred over WAN. For more information, see [Manually Populating Global Cache](wan_populate_cache.md).
* If you plan to use pre-job and post-job scripts or pre-freeze and post-thaw scripts, you must create scripts before you configure the VMware Cloud Director replication job. Veeam Backup & Replication supports script files in the following formats: EXE, BAT, CMD, JS, VBS, WSF, PS1, SH. For more information, see [Pre-Freeze and Post-Thaw Scripts](pre_post_scripts.md).
* You must check limitations for replication. For more information, see [Considerations and Limitations](replica_limitations.md).
* Due to VMware vSphere limitations, if you change the size of VM disks on the source VM, all VM snapshots that were created previously, will not be available for failover, failback and other subsequent operations. For more information, see [this VMware KB article](https://kb.vmware.com/s/article/1004047).

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
