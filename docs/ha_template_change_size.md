---
title: "Changing Template and Helper Appliance Size"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ha_template_change_size.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Changing Template and Helper Appliance Size


During creation of a helper appliance template, Veeam Backup & Replication sends a command to create two VMs: one Linux-based and one Microsoft Windows-based. By default, both VMs use the Standard\_D4lds\_v5 size. This size requires 4 CPUs for each VM, totaling 8 CPUs in the target Microsoft Azure subscription. If your Azure subscription does not have enough available CPUs of this family, you can change the VM size.

During recovery and migration of VMs to Microsoft Azure, Veeam Backup & Replication deploys a helper appliance for each recovered VM. The helper appliance also uses the Standard\_D4lds\_v5 size by default. If your subscription lacks available CPUs of this family, you can change the helper appliance size.

Considerations and Limitations

Consider the following:

* You must apply the VM size change before you start [Instant Restore to Microsoft Azure](instant_recovery_to_azure.md).
* Use VM sizes with at least 4 CPUs and 8 GB RAM.
* It is recommended to select Azure VM sizes that provide temporary disks. For more information, see the [Temporary disk](https://learn.microsoft.com/en-us/azure/virtual-machines/managed-disks-overview#temporary-disk) and [Azure VM sizes with no local temporary disk](https://learn.microsoft.com/en-us/azure/virtual-machines/azure-vms-no-temp-disk) sections in Microsoft Docs.
* B-family (burstable) VM sizes are not recommended.
* Azure VM sizes that support only NVMe storage controllers are not supported yet. For more information on such VM sizes, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-machines/nvme-overview#vm-sizes).
* No reboot or service restart is required.

Changing VM Size Used for Helper Appliance Template Creation

To change the VM size

1. Open the /etc/veeam/veeam\_backup\_and\_replication.conf configuration file as a root user.
2. Set the AzureApplianceTemplate\_DefaultVmSize variable to the required VM size. For example:

To change the VM size on the Microsoft Windows-based backup server, use a registry value: HKEY\_LOCAL\_MACHINE\SOFTWARE\Veeam\Veeam Backup and Replication\AzureApplianceTemplate\_DefaultVmSize {REG\_SZ}.

Changing Helper Appliance Size

To change the VM size:

1. Open the /etc/veeam/veeam\_backup\_and\_replication.conf configuration file as a root user.
2. Set the AzureIr\_Start\_Appliance\_DefaultVmSize variable to the required VM size. For example:

To change the VM size on the Microsoft Windows-based backup server, use a registry value: HKEY\_LOCAL\_MACHINE\SOFTWARE\Veeam\Veeam Backup and Replication\AzureIr\_Start\_Appliance\_DefaultVmSize {REG\_SZ}.


