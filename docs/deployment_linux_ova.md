---
title: "Installing Veeam Software Appliance from OVA"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/deployment_linux_ova.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# Installing Veeam Software Appliance from OVA


You can use the OVA file to automatically deploy a VM in vSphere with predefined hardware and Veeam Software Appliance ready for configuration.To deploy Veeam Software Appliance using the OVA file, perform the following steps:

1. Download the latest version of the ISO file from the [Product Downloads](https://my.veeam.com/my-products) section of your Veeam account.
2. Deploy the OVA template in vSphere. For more information on how to perform this process, see the [vSphere documentation](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/vsphere-virtual-machine-administration-guide-8-0/deploying-ovf-templatesvsphere-vm-admin.html).
3. Start the VM.
4. Select Veeam Backup & Replication in the boot menu.
5. Starting from the [Read and Accept License Agreements](deployment_linux_iso_install_license.md) step, follow the process described in the [Installing Veeam Software Appliance from ISO](deployment_linux_iso_install.md) section to complete the Initial Configuration wizard.


