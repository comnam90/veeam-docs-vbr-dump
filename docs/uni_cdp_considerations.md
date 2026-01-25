---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_considerations.html"
last_updated: "1/22/2026"
product_version: "13.0.1.1071"
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

* Check the list of [supported operating systems](platform_support.md#uni).
* Universal CDP works only for powered on workloads.
* You can add protection groups as a source for replication. If you add new workloads to the protection group after you start the policy, you must install the Veeam CDP Agent Service and Veeam CDP Volume Filter Driver on those workloads. To complete that, do the following:

1. Disable the universal CDP policy.
2. Rescan the protection group.
3. Reboot the newly added workloads.
4. Enable the policy.

* Cluster Shared volumes (CSV) are not supported.
* Microsoft Windows Storage Spaces are not supported.
* Veeam Backup & Replication does not support protection of workloads with 4K native disks (disks with 4096 bytes logical sector size).
* If you reboot a workload with RAW, FAT, FAT32 or exFAT file system, Veeam Backup & Replication starts the initial synchronization process for this workload. For other file systems, Veeam Backup & Replication continues the incremental synchronization.

* One workload can be processed only by one universal CDP policy.
* The maximum number of long-term restore points per disk is 95.

Target Host or Cluster

* The requirements for target destination and its datastores are practically the same as for CDP for VMware vSphere. For more information, see the following topics:

* [Supported Platforms, Applications and Workloads](platform_support.md#cdp)

Note that the minimum ESXi version required is 8.0 for the universal CDP.

* [Veeam CDP Source and Target](system_requirements_vm.md#cdp_source_target)

* I/O filter must be installed on the target host or cluster. For more information on the I/O filter, see [Installing I/O Filter](cdp_io_filter_install.md).

If you upgrade from Veeam Backup & Replication of a previous version, and I/O filter was installed, you must upgrade the I/O filter as described in [Updating and Uninstalling I/O Filter](cdp_io_filter_remove.md).

* You must configure CDP for one cluster on one backup server only. If you add a cluster to another backup server and install the I/O filter (filter required for CDP) on it, CDP policies on the first backup server will fail.

* When you upgrade Veeam Backup & Replication to the current version, you can postpone the upgrade of the I/O filter on the vCenter Servers to a later time. Veeam Backup & Replication supports the postponed upgrade for the minor versions within the 12 version. You must postpone the upgrade or upgrade all clusters on the vCenter Servers. Partially upgraded vCenter Servers or clusters have limited functionality. You cannot add VMs from such vCenter Servers or clusters to CDP policies, commit failback and perform some other operations.
* If you upgrade the primary version of hosts in the vCenter Server (for example, from ESXi version 7 to 8), you must upgrade the I/O filter version on this server. Perform this upgrade either alongside the ESXi upgrade or immediately after it. For more information, see [Updating and Uninstalling I/O Filter](cdp_io_filter_remove.md).
* If you add a new cluster or host to a vCenter Server after the I/O filter is installed on the existing clusters and hosts, you must [launch the](cdp_io_filter_install.md) [I/O Filter Management](cdp_io_filter_install.md) [wizard](cdp_io_filter_install.md). Make sure that check boxes are selected near all clusters where the I/O filter must be present and finish the wizard. After you finish the wizard, Veeam Backup & Replication requests the vCenter Server to install the I/O filter (if required), and to configure it.

Replicas

* Because replication operates at the volume level, the following applies:

* Veeam Backup & Replication preserves the original volume and disk layout whenever possible. In some cases, such as with dynamic volumes on the source workload, the replica disk layout may differ from the original layout.
* When replicating source workloads with volumes encrypted by Microsoft Windows BitLocker, the replicated volumes on the target appear unencrypted. However, you can replicate workloads to a target datastore that is encrypted at the storage layer.

* On the target host, Veeam Backup & Replication does not allow you to migrate replicas using VMware vSphere Storage vMotion. Note that host vMotion is allowed. However, note that during failover, host vMotion is not allowed.
* Replicas can be powered on only using the failover operation; powering on replicas manually is not supported.


