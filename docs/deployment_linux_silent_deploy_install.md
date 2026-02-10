---
title: "Automating Installation Without Initial Configuration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/deployment_linux_silent_deploy_install.html"
last_updated: "2/9/2026"
product_version: "13.0.1.1071"
---

# Automating Installation Without Initial Configuration


You can modify the Veeam Software Appliance ISO file to allow unattended installation. This allows you to deploy Veeam Software Appliance automatically. After the installation is complete, you must configure Veeam Software Appliance manually using the Initial Configuration wizard.

|  |
| --- |
| Important |
| Installing additional Linux packages, third-party applications, or changing OS settings (other than those that can be controlled by the Veeam Host Management Console) on Veeam Appliances is not supported. Veeam Customer Support cannot provide technical support for appliances with unsupported modifications due to their unpredictable impact on the  security, stability, and performance of the appliance. For more information, see [this KB article.](https://www.veeam.com/kb4772) |

To automate the installation of Veeam Software Appliance, do the following:

1. Download the latest version of the ISO file from the [Product Downloads](https://my.veeam.com/my-products) section of your Veeam account.
2. Unpack the ISO file.
3. Make the following changes to the %path\_to\_unpacked\_ISO\_folder%\EFI\BOOT\grub.cfg file to automate the installation process:

1. To set the default menu entry, change the set default parameter to "Veeam Backup & Replication v13.0>Install - fresh install, wipes everything (including local backups)".
2. To set a GRUB menu timeout, change the set timeout parameter to any positive value.
3. To set all questions to be answered automatically, add inst.assumeyes to the end of the install menu entry LABEL=VeeamSA:/vbr-ks.cfg quiet.

|  |
| --- |
| Note |
| You can automate additional options in the grub.cfg file. To do this, add inst.assumeyes to the end of the appropriate lines. |

1. Save the changes.

1. Repack the ISO file.
2. Mount the ISO file to the machine where you plan to install Veeam Software Appliance, or burn the ISO file to a flash drive or other removable storage device. If you plan to install Veeam Software Appliance on a virtual machine, use the built-in tools of the virtualization management software to mount the ISO file.

|  |
| --- |
| Note |
| To create a bootable USB stick, it is recommended that you use [Rufus](https://rufus.ie/en/) with the default settings. Note that you need to select Write in DD Image mode option when prompted. |

1. The automatic installation finishes at the [Read and Accept License Agreements](deployment_linux_iso_install_license.md) step. To complete the Initial Configuration wizard, continue the process described in the [Installing Veeam Software Appliance from ISO](deployment_linux_iso_install.md) section.


