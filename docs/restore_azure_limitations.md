---
title: "Considerations and Limitations for Restore to Microsoft Azure"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations for Restore to Microsoft Azure


When planning to restore workloads to Microsoft Azure, consider the following information.

Workloads and Architectures

* Veeam Backup & Replication supports restore to Microsoft Azure for the following workloads:Microsoft Windows workloads that run Windows Server 2008/Windows Vista and later.
* Linux workloads (see the Supported Distributions & Versions section in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/endorsed-distros)).

* If the system disk of an initial workload uses the GPT partitioning scheme, the number of partitions on the disk cannot exceed 4. During restore such disk will be converted to a disk with the MBR partitioning scheme.

* The restore to Microsoft Azure functionality does not support the Azure Hybrid Use Benefit program.
* [For restore from backups created by Veeam Agent for Microsoft Windows] Workloads from a backup that contains a [failover cluster](agents_cluster_support.md) are restored as separate VMs, not as a cluster. Shared cluster disks of these VMs are restored as regular disks.

Linux-Specific Requirements

* We strongly recommend having one of the following tools installed on Linux workloads that will be restored: dracut, mkinitrd or initramfs. Otherwise, they may not boot after restore.

* If you use a cloud-init-based Linux distribution, we recommend that you use SSH keys on these distributions. If you use a password, it is blocked after restore for security reasons. To reset the password on the restored VM, you need to use the VMAccess extension. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/troubleshoot/azure/virtual-machines/reset-password).

Microsoft Windows-Specific Requirements

* [For Microsoft Windows-based backup server] Veeam Backup & Replication does not support restoring disks encrypted by BitLocker, except for restoring from backups created by Veeam Agent for Microsoft Windows. For more information, see the [Veeam Agent for Microsoft Windows User Guide](https://helpcenter.veeam.com/docs/agentforwindows/userguide/bitlocker.html?ver=13).

* Microsoft Windows workloads where the boot partition and the operating system partition are located on separate drives are not supported for restore operations.

Disks and VM Sizes

* Veeam Backup & Replication does not support restoring of disks whose logical sector size is 4096 bytes. Contents of such disks will be unreadable in Microsoft Azure.

* [Unmanaged VM disks] Veeam Backup & Replication supports restoring disks that are equal to or less than 4093 GB. During the restore process, VM disks can increase in size up to 2 GB because of conversion, and Azure supports disk up to 4095 GB. For more information on all disk sizes that Azure supports, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#unmanaged-virtual-machine-disks).
* [Managed VM disks] Veeam Backup & Replication supports restoring disks equal or less than 4093 GB for OS disks and equal to or less than 32765 GB for other disks. During the restore process, VM OS disks can increase in size up to 2 GB because of conversion. For more information on all managed disk sizes that Azure supports, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#managed-virtual-machine-disks). For more information on OS disk size that Azure supports, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-machines/managed-disks-overview#os-disk). Note that supported disk sizes for Azure and Veeam Backup & Replication differ.
* [For native Microsoft Azure VM workloads] Veeam Backup & Replication does not support restore of Azure Ultra Disks.

Generation 2 VM Support

* When you select VM sizes at the [Specify VM Size](restore_azure_size.md) step of the Restore to Azure wizard, make sure that the selected size is compatible with Generation 2 VMs.
* Generation 2 VMs support only managed disks. Thus, you will need to select the managed storage type from the Storage type list at the [Specify VM Size](restore_azure_size.md) step of the Restore to Azure wizard.

Pricing

The price of a restored VM disk can become higher because of the increase in disk size during the restore process. For more information on pricing, see [Managed Disks pricing](https://azure.microsoft.com/en-us/pricing/details/managed-disks/) and [Unmanaged Disk and Page Blob pricing](https://azure.microsoft.com/en-us/pricing/details/storage/page-blobs/).

Storage Accounts

When [you select a storage account](restore_azure_size.md) whose resources you want to use to store disks of the restored workload, consider the following:

* Storage accounts with the zone-redundant storage (ZRS), geo-zone-redundant storage (GZRS) and geo-redundant storage (GRS) replication options are not supported. However, read-access geo-redundant storage (RA-GRS) option is supported. For details on replication options, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy#zone-redundant-storage).

* If you plan to use a premium storage account and want to store unmanaged disks there, the restore speed for such disks will be limited to 30 MB/s (approximately).

Virtual Networks and Connectivity

* You can use restore to Microsoft Azure for environments with ExpressRoute or site-to-site VPN connectivity to Microsoft Azure. In this case, Azure restore proxy appliances (former Azure proxies) and helper appliances must have private IP addresses. For more information, see [this Veeam KB article](https://www.veeam.com/kb4014).
* During restore, Veeam Backup & Replication uses Azure Blob SAS links to the target VM disks. That is why DNS must resolve these Azure Blob endpoints and the firewall rules must allow such traffic.

Regions

When you [select a geographic region to which you want to restore workloads](restore_azure_location.md), consider that some regions are access restricted to support specific customer scenarios. For example, VMs cannot be created there. To be able to perform different actions in those regions, create a support request in the Azure portal.

For the full list of access-restricted regions, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/availability-zones/cross-region-replication-azure#azure-cross-region-replication-pairings-for-all-geographies). The regions are marked with an asterisk (\*).

Microsoft Resource Naming

Microsoft has strict rules for naming Azure resources. For more information on resource naming requirements, see Microsoft Docs: [Resource name rules](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/resource-name-rules#microsoftcompute) and [Resolve errors for reserved resource names](https://learn.microsoft.com/en-us/azure/azure-resource-manager/troubleshooting/error-reserved-resource-name).

Azure Stack

Veeam Backup & Replication supports restoring of managed and unmanaged disks equal to or less than 1021 GB. This is due to the following reasons: VM disks can increase in size up to 2 GB because of conversion during the restore process; Azure Stack supports disk up to 1023 GB. For more information on all disk sizes that Azure supports, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure-stack/user/azure-stack-managed-disk-considerations?view=azs-2005#cheat-sheet-managed-disk-differences).

You can change the maximum supported size for unmanaged VM disks in the configuration file on the Linux-based backup server or with registry values on the Microsoft Windows-based backup server. For more information, contact [Veeam Customer Support](https://www.veeam.com/support.html).

|  |
| --- |
| Important |
| The price of a restored VM disk can become higher because of the increase in disk size during the restore process. For more information on pricing, see [Azure Stack Hub Pricing](https://azure.microsoft.com/en-us/pricing/details/azure-stack/hub/). |

Page updated 2026-06-22

