---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/cdp_requirements.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

If you plan to use CDP to protect your workloads, consider the following requirements and limitations.

Licensing

CDP is included in the Veeam Universal License. When using a legacy socket-based license, the Enterprise Plus edition is required.

Platforms and Datastores

* CDP is supported for a limited number of platforms and versions. For more information on platforms and requirements for them, see [Supported Platforms, Applications and Workloads](platform_support.md#cdp).
* CDP supports specific source and target datastores. For more information, see [Veeam CDP Source and Target](system_requirements_vm.md#cdp_source_target).

Infrastructure Components

* The backup server must have at least 16 GB RAM.
* CDP proxy must meet the requirements listed in section [CDP Proxy](cdp_proxy.md).
* The network between the infrastructure components must suit the load on your infrastructure. We recommend that you use at least 100 Mbps network. Slower networks cannot handle the generated disk traffic without interruption. The better performance is proven on 10 Gbps networks or faster and MTU 9000.
* You must configure CDP for one cluster on one backup server only. If you add a cluster to another backup server and install the I/O filter (filter required for CDP) on it, CDP policies on the first backup server will fail. For more information on the I/O filter, see [I/O Filter](cdp_infrastructure.md#iofilter).

* When you upgrade Veeam Backup & Replication to the current version, you can postpone the upgrade of the I/O filter on the vCenter Servers to a later time. Veeam Backup & Replication supports the postponed upgrade for the minor versions within the 12 version. You must postpone the upgrade or upgrade all clusters on the vCenter Servers. Partially upgraded vCenter Servers or clusters have limited functionality. You cannot add VMs from such vCenter Servers or clusters to CDP policies, commit failback and perform some other operations.
* The maximum number of CDP policies that can be created on one backup server is 100.
* If you upgrade the primary version of hosts in the vCenter Server (for example, from ESXi version 7 to 8), you must upgrade the I/O filter version on this server. Perform this upgrade either alongside the ESXi upgrade or immediately after it. For more information, see [Updating and Uninstalling I/O Filter](cdp_io_filter_remove.md).
* If you add a new cluster or host to a vCenter Server after the I/O filter is installed on the existing clusters and hosts, you must [launch the](cdp_io_filter_install.md) [I/O Filter Management](cdp_io_filter_install.md) [wizard](cdp_io_filter_install.md). Make sure that check boxes are selected near all clusters where the I/O filter must be present and finish the wizard. After you finish the wizard, Veeam Backup & Replication requests the vCenter Server to install the I/O filter (if required), and to configure it.

Virtual Machines

* Sizes of all VM disks must be set as integer values.

* Veeam Backup & Replication does not support protection of workloads with 4K native disks (disks with 4096 bytes logical sector size).
* VMs that you plan to protect must not have snapshots at the moment the CDP policy starts for the first time. For example, if a VM is already added to a backup job, make sure that the scheduled backup session does not overlap with the CDP policy first run.
* The hardware versions of VMs that you plan to protect must be supported on the target cluster.

* CDP works only for powered on VMs. However, for VMs with IDE hard drives you must power off VMs before the initial synchronization. This is required to apply a new storage policy to VMs. For more information, see [How CDP Works](cdp_hiw.md).
* CDP is not supported for VMs to which VM storage policies with multiple datastore specific rule sets apply. If you need to define datastores to be used for placement of the VMs, you can add a tag rule for vSAN instead of a tag based placement datastore specific rule. For more information on how to create tag rules for vSAN, see [VMware Docs](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vsan.doc/GUID-9A3650CE-36AA-459F-BC9F-D6D6DAAA9EB9.html).
* Shared disks, physical RDM and SCSI bus sharing are not supported. Note that vRDM disks are supported.
* One VM can be processed only by one CDP policy.

* During the initial synchronization, Veeam Backup & Replication needs double space allocation for VMs with thick-provisioned disks on the target host. After the initial synchronization finishes, Veeam Backup & Replication frees half of the allocated space for such VMs. This is a part of mechanism required to support protection of disks newly added to the source VMs.

* The maximum number of disks attached to one VM is 50.
* If you change the VM disk size after the replication process starts, Veeam Backup & Replication starts the replication process anew. This action removes restore points created before the size change and starts the initial synchronization.
* The maximum number of long-term restore points per disk is 95.
* For VMs encrypted on VMware side, consider the following:

+ Make sure that the Allow I/O filters before encryption parameter is set to True for the VM storage policy component. For more details, see [VMware vSphere documentation](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.storage.doc/GUID-1DA70011-BCDE-45F6-AA28-7E486144ED0E.html).
+ To create encrypted CDP policy, select the encrypted datastore at the Destination step of the wizard. For more information, see [Creating CDP Policies](cdp_policy_create.md).
+ Encryption for transaction log files that contain incremental changes for disks is not supported. For more information, see [CDP Replication Chain](cdp_replica_chain.md).

Replicas

* On the target host, Veeam Backup & Replication does not allow you to migrate replicas using VMware vSphere Storage vMotion. Note that host vMotion is allowed. However, note that during failover, host vMotion is not allowed.
* Replicas can be powered on only using the failover operation; powering on replicas manually is not supported.
* Veeam Backup & Replication supports testing. For more information, see [SureReplica](recovery_verification_surereplica.md).
* [SureReplica](recovery_verification_surereplica.md) verification does not prevent CDP policy from running.

Related Topics

[Backup Infrastructure for CDP](cdp_infrastructure.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
