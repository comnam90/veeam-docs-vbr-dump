---
title: "Managing Helper Appliances"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_azure_linux.html"
last_updated: "6/30/2025"
product_version: "13.0.1.1071"
---

# Managing Helper Appliances

In this article

Helper appliances are Linux-based VMs in Microsoft Azure registered by Veeam Backup & Replication. Helper appliances are required to restore Linux workloads to Microsoft Azure. During the restore process, Veeam Backup & Replication mounts disks of a backed-up workload to a helper appliance to prepare disks for restore.

To instruct Veeam Backup & Replication to deploy helper appliances, you must configure them as described in section [Configuring Helper Appliances](restore_azure_helper.md). When deploying the helper appliance, Veeam Backup & Replication analyzes the VM sizes available in the restore region and selects the cheapest and smallest size suitable for using the helper appliance.

Helper appliances are persistent. After the restore process finishes, helper appliances get powered off and remain in Microsoft Azure. The appliances remain in the powered off state until you start a new restore process. Note that Microsoft Azure will bill you for storing helper appliances disks in the storage account. To remove a helper appliance, follow the instruction provided in [Removing Helper Appliances](restore_azure_remove_appliance.md).

In This Section

* [Configuring Helper Appliances](restore_azure_helper.md)
* [Changing Credentials for Helper Appliances](restore_azure_credentials.md)
* [Removing Helper Appliances](restore_azure_remove_appliance.md)

Page updated 6/30/2025

Page content applies to build 13.0.1.1071
