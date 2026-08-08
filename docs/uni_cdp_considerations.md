---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_considerations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


If you plan to use universal CDP to protect your workloads, consider the following requirements and limitations.

Licensing

The availability of the feature depends on the license you use. For more details about licensing support, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).

Infrastructure Components

* The backup server must have at least 16 GB RAM.

* CDP proxy must meet the requirements listed in section [CDP Proxy](cdp_proxy.md).

* The direct connection between the source workloads and the backup server is required.

* The network between the infrastructure components must suit the load on your infrastructure. We recommend that you use at least 100 Mbps network. Slower networks cannot handle the generated disk traffic without interruption. The better performance is proven on 10 Gbps networks or faster and MTU 9000.

Source Workloads

* Check the list of [supported operating systems](platform_support_universal_cdp.md).

* When installing Veeam CDP Agent Service and Veeam CDP Volume Filter Driver, consider that they are compatible only with the nosnap backup agent. If you plan to back up Linux workloads using Veeam Agent for Linux, make sure that the Install nosnap agent check box is selected. For more information, see [Installing CDP Agent Service and Filter Driver](uni_cdp_service_install.md).

* Check that the logical sector size of disks that you plan to restore equals 512 bytes. Veeam Backup & Replication does not support the protection of workloads with 4K native disks (disks with 4096 bytes logical sector size).

* [For Linux-based workloads] LVM topology is supported. LVM topology is preserved structurally but is simplified on the target. Striped, mirrored or RAID logical volumes are replicated into linear volumes on the target side.
* [For Linux-based workloads] Clustered LVM topology is not supported.
* Universal CDP works only for powered on workloads.

* Cluster Shared volumes (CSV) are not supported.
* Microsoft Windows Storage Spaces are not supported.

* You can add protection groups as a source for replication. If you add new workloads to the protection group after you start the policy, you must install the Veeam CDP Agent Service and Veeam CDP Volume Filter Driver on those workloads. To complete that, do the following:

1. Disable the universal CDP policy.
2. Rescan the protection group.
3. Reboot the newly added workloads.
4. Enable the policy.

* [For Microsoft Windows workloads] If you reboot a workload with the RAW, FAT, FAT32 or exFAT file system, Veeam Backup & Replication starts the initial synchronization process for this workload. For other file systems, Veeam Backup & Replication continues the incremental synchronization.
* [For Linux-based workloads] If you reboot a workload, Veeam Backup & Replication starts the initial synchronization process for this workload. Veeam Backup & Replication reads the entire source, but transfers only changed blocks.

* One workload can be processed only by one universal CDP policy.
* The maximum number of long-term restore points per disk is 95.

Target Host or Cluster

* The requirements for the target destination and its datastores are practically the same as for CDP for VMware vSphere. For more information, see the following topics:

* [Workloads](platform_support_vm.md#cdp)

The minimum ESXi version required is 8.0 for the universal CDP.

* [Veeam CDP Source and Target Datastores](system_requirements_vm.md#cdp_source_target)

* The I/O filter must be installed on the target host or cluster. For more information on the I/O filter, see [Installing I/O Filter](cdp_io_filter_install.md).

If you upgrade from a previous version of Veeam Backup & Replication, and I/O filter was installed, you must upgrade the I/O filter as described in [Updating and Uninstalling I/O Filter](cdp_io_filter_remove.md).

* You must configure CDP for one cluster on one backup server only. If you add a cluster to another backup server and install the I/O filter (filter required for CDP) on it, CDP policies on the first backup server will fail.

* When you upgrade Veeam Backup & Replication to the current version, you can postpone the I/O filter upgrade on vCenter Servers. Veeam Backup & Replication supports postponing the I/O filter upgrade for the minor versions within 13.x, and for 12.3.2.x or 12.3.1.x filter versions. It is recommended that all clusters in one vCenter Server use the same I/O filter version. Partially upgraded vCenter Servers have limited functionality. You cannot add VMs from non-upgraded hosts to CDP policies, commit failback and perform some other operations. You should keep the I/O filter at the latest version to reduce the risk of potential issues.
* If you upgrade the primary version of hosts in the vCenter Server (for example, from ESXi version 7 to 8), you must upgrade the I/O filter version on this server. Perform this upgrade either alongside the ESXi upgrade or immediately after it. For more information, see [Updating and Uninstalling I/O Filter](cdp_io_filter_remove.md).
* If you add a new cluster or host to a vCenter Server after the I/O filter is installed on the existing clusters and hosts, you must [launch the I/O Filter Management wizard](cdp_io_filter_install.md). Make sure that check boxes are selected near all clusters where the I/O filter must be present and finish the wizard. After you finish the wizard, Veeam Backup & Replication requests the vCenter Server to install the I/O filter (if required) and to configure it.

Replicas

* Because replication operates at the volume level, the following applies:

* Veeam Backup & Replication preserves the original volume and disk layout whenever possible. In some cases, such as with dynamic volumes on the source workload, the replica disk layout may differ from the original layout.
* [For Microsoft Windows-based workloads] When replicating source workloads with volumes encrypted by Microsoft Windows BitLocker, the replicated volumes on the target appear unencrypted. However, you can replicate workloads to a target datastore that is encrypted at the storage layer.
* [For Linux-based workloads] When replicating source workloads with the encryption layer that sits underneath the block device, the replicated volumes on the target appear unencrypted. The encryption on the topmost block layer is not supported.

* On the target host, Veeam Backup & Replication does not allow you to migrate replicas using VMware vSphere Storage vMotion.You can use host vMotion, except during failover.
* Replicas can be powered on only using the failover operation; powering on replicas manually is not supported.

Re-IP, Seeding and Mapping

* Only IPv4 rules are supported.

* You can specify static IPs or IP ranges. Do not use 0 to specify IP address ranges. In Veeam Backup & Replication, value 172.16.17.0 means a regular IP address 172.16.17.0, not an IP address range. To specify a range, use the asterisk character (\*).

The asterisk matches one entire octet, and re-IP rules match source IPs by octet only — the subnet mask is not used to select which IPs a rule applies to. For example, the source address 10.0.0.\* matches 10.0.0.0 through 10.0.0.255, but not 10.0.1.1, even if both addresses belong to the same subnet.

* Replica re-IP works only for Microsoft Windows VMs.
* Replica re-IP works only if you perform replica failover using Veeam Backup & Replication. If you power on a replica in some other way, for example, manually using a native client, re-IP rules will not be applied to it.
* The backup server OS must support mounting of the system disks of VMs that will be replicated.

* For seeding, make sure that you have backups of replicated workloads in a backup repository in the DR site. If you do not have the backups, create them as described in section [Creating Replica Seeds for CDP](uni_creating_replica_seed.md).

* Backups for seeding must be created by [Veeam Agent for Linux or Veeam Agent for Microsoft Windows](agents_introduction.md).

* Backups for seeding must not reside in a scale-out backup repository.

Page updated 2026-06-23

