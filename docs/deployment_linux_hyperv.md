---
title: "Installing Veeam Software Appliance from Hyper-V Template"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/deployment_linux_hyperv.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Installing Veeam Software Appliance from Hyper-V Template


You can use the Hyper-V template to deploy a VM on a Hyper-V host with predefined hardware and Veeam Software Appliance ready for configuration. The template is supplied as a set of .vhdx files with Veeam Software Appliance preinstalled: a system disk (os-disk.vhdx) and a data disk (data-disk.vhdx).

|  |
| --- |
| Note |
| Consider the following before deploying a Veeam Software Appliance from the Hyper-V template:   * The Hyper-V server must meet the platform requirements for virtual infrastructure. For more information, see [Microsoft Hyper-V](platform_support_hv.md#hv_virt). * The virtual machine must be of Generation 2 because the Veeam Software Appliance disks use the UEFI/GPT layout. Allocate at least 8 virtual processors and 16 GB RAM, plus 500 MB RAM for each concurrent job. For more information, see [Considerations and Limitations](deployment_linux_byb.md). |

To deploy Veeam Software Appliance using the Hyper-V template, perform the following steps:

1. Extract the files from the .ZIP file.
2. Copy the Hyper-V template files (os-disk.vhdx and data-disk.vhdx) to a dedicated folder in the storage of the Hyper-V host. It is recommended that you deploy the VM from copies and keep the original files as a master template.
3. In Hyper-V Manager, create a new virtual machine. When you run the New Virtual Machine Wizard, specify the following settings:

* Specify Generation: select Generation 2.
* Assign Memory: specify 16384 MB or more. Do not enable Dynamic Memory.
* Configure Networking: connect the network adapter to the virtual switch that provides the appliance with network access.
* Connect Virtual Hard Disk: select Use an existing virtual hard disk and specify the copied os-disk.vhdx file.

1. In the settings of the created virtual machine, add the data disk: on the SCSI Controller, add a new Hard Drive, select Use an existing virtual hard disk and specify the copied data-disk.vhdx file.
2. In the Processor settings, set the Number of virtual processors to 8 or more.
3. In the Security settings, make sure Enable Secure Boot is selected and set the Template to Microsoft UEFI Certificate Authority.
4. In the Firmware settings, move the hard drive with the os-disk.vhdx file to the top of the boot order.
5. Start the virtual machine and connect to it.
6. Select Veeam Backup & Replication in the boot menu.
7. Starting from the [Read and Accept License Agreements](deployment_linux_iso_install_license.md) step, follow the process described in the [Installing Veeam Software Appliance from ISO](deployment_linux_iso_install.md) section to complete the Initial Configuration wizard.

Page updated 2026-07-30

