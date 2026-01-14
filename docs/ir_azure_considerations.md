---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ir_azure_considerations.html"
last_updated: "1/8/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

Prerequisites

Before you recover workloads, you must deploy a helper appliance template in the region where you plan to recover workloads. For more information, see [Helper Appliance Template](helper_appliance_template.md).

Storage Accounts

* The storage accounts used for [helper appliance template creation](ha_template_add.md) and for [communication with helper appliance](ir_azure_helper.md) must have key authentication enabled.
* Storage accounts with private endpoints are not supported.

Supported Backup Sources

Instant Recovery to Microsoft Azure supports recovering backups stored on the following Microsoft Azure object storage-based backup repositories:

* Veeam Data Cloud Vault (object storage added as a backup repository)
* Microsoft Azure Blob Storage (Azure Blob Storage object storage added as a backup repository)
* External repository containing backups created by Veeam Backup for Microsoft Azure

Workloads and Architectures

* Veeam Backup & Replication supports Instant Recovery to Microsoft Azure for the following workloads:

+ Microsoft Windows workloads that run Microsoft Windows Server 2016/Windows 10 and later.
+ Linux workloads (see the Supported Distributions & Versions section in [Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/endorsed-distros)).

* Restoring of workloads running on the ARM CPU architecture is not supported.

* Instant Recovery of Veeam Software Appliance with Veeam Backup & Replication is not supported.

Virtual Networks

If you plan to select or already have selected an existing network and subnet for a [helper appliance](ir_azure_helper.md) or [helper appliance template](ha_template_add.md), you must allow access to public endpoints from those subnets. For the helper appliance template, see the Temporary Azure VMs used to create templates of Instant Recovery to Azure helper appliances row in the [Instant Recovery to Microsoft Azure port table](used_ports.md#instant_recovery_to_azure). For the helper appliance, see the Instant Recovery for Azure helper appliance row in the [Instant Recovery to Microsoft Azure port table](used_ports.md#instant_recovery_to_azure).

This is required due to changes in Microsoft Azure. After March 31, 2026, new virtual networks will default to the creation of private subnets, which can no longer use default outbound access connectivity.  VMs that require public endpoint access will need to use explicit outbound connectivity. For more information, see [Microsoft Docs](https://azure.microsoft.com/en-us/updates?id=default-outbound-access-for-vms-in-azure-will-be-retired-transition-to-a-new-method-of-internet-access).

If you select the default option to create a temporary virtual network and subnet for the helper appliance template, you do not need to allow access to any endpoints. The created temporary subnet will not be private. It will have the allowed outbound internet access and will continue to work even after March 31, 2026.

Linux-Specific Requirements

* You should have one of the following tools installed on Linux workloads that will be recovered: dracut, mkinitrd or initramfs. Otherwise, these workloads may not boot after restore.
* Ensure that the iSCSI initiator is installed on the workloads you plan to recover. For Debian, Ubuntu, and SUSE Linux distributions, install the open-iscsi package. For RHEL-based distributions, install the iscsi-initiator-utils package.

Additionally, the Linux kernel must be configured with support for iSCSI boot.

* Veeam Backup & Replication does not support recovery for Linux workloads with system mount points (/root, /boot, /etc, /usr, /var and others) that reside on ZFS pools. These systems will not boot after recovery. After recovery, you must manually import ZFS pools.
* The cloud-init package is removed during the recovery process. If you require cloud-init functionality after restore, you must reinstall and reconfigure cloud-init manually. Do that only after migration is complete.
* The waalinuxagent package is removed during the recovery process of some Linux distributives. If you require waalinuxagent functionality after restore, you must reinstall and reconfigure waalinuxagent manually. Do that only after migration is complete.

* For optimal Instant Recovery performance, avoid keeping multiple Linux kernel versions installed on the workloads you plan to recover. During recovery, Veeam Backup & Replication rebuilds initramfs/dracut for each detected kernel. A large number of installed kernels can significantly increase the time required for the conversion and recovery operation.

Microsoft Windows-Specific Requirements

* Microsoft Windows workloads configured with the BIOS boot type that have Windows updates from March 2025 or newer will not boot after Instant Restore to Azure.
* Microsoft Windows workloads where the boot partition and the operating system partition are located on separate drives are not supported for restore operations.

* [For Microsoft Windows-based backup server] Veeam Backup & Replication does not support restoring VMs encrypted by BitLocker, except for restoring from backups created by Veeam Agent for Microsoft Windows. For more information, see the [Veeam Agent for Microsoft Windows User Guide](https://helpcenter.veeam.com/docs/agentforwindows/userguide/bitlocker.html?ver=13).
* Instant Recovery to Microsoft Azure is not supported for Domain Controllers.
* Instant Recovery to Microsoft Azure does not support the use of Azure Hybrid Use Benefit (AHUB).
* During recovery, Veeam Backup & Replication assigns drive letters to an iPXE disk. This disk may be visible within the Windows operating system. Do not modify the contents of this disk before migrating the VM to production. Otherwise, this can lead to failed restores or data loss.

Disks and VM Sizes

* Veeam Backup & Replication does not support the Microsoft Azure VM sizes that support NVMe storage controllers. If you restore a VM with this configuration, the VM will fail to boot. For more information on the unsupported sizes, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-machines/nvme-overview#vm-sizes).

* Veeam Backup & Replication does not support restoring of 4K native disks (disks with 4096 byte logical sector size). Contents of such disks will be unreadable after [migration](ir_azure_finalize.md).

* Instant Recovery to Microsoft Azure supports creating Premium SSD, Standard SSD, and Standard HDD disks. Ultra Disk and Premium SSD v2 are not supported.
* Veeam Backup & Replication supports restoring disks equal or less than 4093 GB for OS disks and equal to or less than 32,767 GB for other disks. During the restore process, VM OS disks can increase in size up to 2 GB because of conversion. For more information on all managed disk sizes that Azure supports, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#managed-virtual-machine-disks). For more information on OS disk size that Azure supports, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-machines/managed-disks-overview#os-disk). Note that supported disk sizes for Azure and Veeam Backup & Replication differ.
* After performing migration or switchover, a restored VM may fail to boot and display the following error: "Creating a virtual machine from Marketplace image or a custom image sourced from a Marketplace image requires Plan information in the request." This issue occurs when the restored VM does not contain the required Plan Information (Publisher, Product, Name) in the boot disk metadata. If you encounter this error, contact Veeam Customer Support for further assistance.

Pricing

The price of a restored VM disk can become higher because of the increase in disk size during the restore process. For more information on pricing, see [Managed Disks pricing](https://azure.microsoft.com/en-us/pricing/details/managed-disks/) and [Unmanaged Disk and Page Blob pricing](https://azure.microsoft.com/en-us/pricing/details/storage/page-blobs/).

Security Type Support

Veeam Backup & Replication supports the creation of Microsoft Azure VMs with the Standard security type. The Trusted launch security type is not supported.

Recovery Process Recommendations

* For faster recovery, recover workloads to the same region where the backup is stored.
* You should enable application-aware processing in the backup jobs settings. This helps the recovered VMs start faster.
* You should use different subnets for the helper appliance (the [Helper Appliance](ir_azure_helper.md) step) and the recovered workload (the [Network](ir_azure_network.md) step), otherwise some OSes may not boot.

* After a VM is recovered, you should finalize the recovery as soon as possible, preferably within one or two days. This ensures optimal performance and stability, as Instant Recovery mounts the VM from the backup repository, and this is not intended for long-term production use.

Large-Scale Restore of Workloads

If you plan to recover more than 20 workloads at the same time, follow the instructions provided in [this Veeam KB article](https://www.veeam.com/kb4764).

Page updated 1/8/2026

Page content applies to build 13.0.1.1071
