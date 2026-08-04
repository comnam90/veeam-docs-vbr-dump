---
title: "Step 8. Configure Network Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_vm_restore_ui_network.html"
last_updated: "2024"
product_version: "13.1.0.411"
---

# Step 8. Configure Network Settings


[This step applies only if you have selected the Restore to a new location, or different settings option at the Restore Mode step of the wizard]

At the Network step of the wizard, do the following:

1. Select the Azure VM.
2. Click Edit.
3. In the Network settings window, select a virtual network and a subnet to which you want to connect the restored Azure VM. For a virtual network to be displayed in the Virtual network list, it must be created in the Microsoft Azure portal as described in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-network/manage-virtual-network). For a subnet to be displayed in the Subnet list, it must be created within the selected virtual network as described in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-manage-subnet).

You can also specify a security group (virtual firewall) that will be associated with the restored VM. Security groups are used to filter network inbound traffic to and outbound traffic from Azure resources. Each security group contains a set of rules that control the traffic. For a network security group to be displayed in the Security group list, it must be created in the Microsoft Azure portal as described in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-network/tutorial-filter-network-traffic#create-a-network-security-group).

[![Restoring Azure VM](images/azure_restore_vm_network.webp)](images/azure_restore_vm_network.webp "Restoring Azure VM")

Page updated 2024-02-02

