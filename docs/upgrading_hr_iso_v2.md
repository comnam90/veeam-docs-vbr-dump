---
title: "Upgrading Hardened Repository Deployed with Veeam Hardened Repository ISO"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/upgrading_hr_iso_v2.html"
last_updated: "2/25/2026"
product_version: "13.0.1.1071"
---

# Upgrading Hardened Repository Deployed with Veeam Hardened Repository ISO


If your backup infrastructure includes hardened repositories deployed using the Veeam Hardened Repository ISO v2, you can upgrade them using the Veeam Infrastructure Appliance ISO. After the upgrade, they will have the same features and functionality as a Veeam Infrastructure Appliance.

During the upgrade, all files located in /mnt/veeam-repository01/ are preserved. However, all directory paths will be changed to /var/lib/veeam/%subdirectoryname%/%filename%.

To upgrade your hardened repository, do the following:

1. Download the latest version of the Veeam Infrastructure Appliance ISO file from the [Product Downloads](https://my.veeam.com/my-products) section of your Veeam account.

|  |
| --- |
| Tip |
| The ISO file can be found in the Additional downloads section under Extensions and Other > Veeam Infrastructure Appliance. |

1. Mount the ISO file to the server used as the hardened repository. Alternatively, burn the ISO file to a flash drive or other removable storage device.

|  |
| --- |
| Note |
| To create a bootable USB stick, it is recommended that you use [Rufus](https://rufus.ie/en/) with the default settings. You must select Write in DD Image mode option when prompted. |

1. In the Boot Manager, select the drive where you mounted the ISO file.
2. In the installation menu, do the following:

1. Select Veeam Hardened Repository.
2. Select Upgrade - upgrades Hardened Repository to latest version.
3. Select Reboot System or wait for the system to reboot automatically.

1. After the system reboots, complete the Initial Configuration wizard as described in the [Installing Veeam Infrastructure Appliance with ISO](linux_infrastructure_appliance_install.md) section.

|  |
| --- |
| Important |
| You must specify the same hostname and network settings as before the upgrade. If they are not identical, Veeam Backup & Replication will not be able to connect to the updated host. |

1. In the Veeam Backup & Replication console, do the following:

1. Open the Backup Infrastructure view.
2. Select Managed Servers in the inventory pane.
3. Right-click the server used as a hardened repository and select Properties.

1. In the Edit Server wizard, do the following:

1. Navigate to the Access step.
2. Set the connection method to Connect using certificated-based authentication.
3. Go through the rest of the wizard and wait for the required components to be installed.
4. Click Finish.

|  |
| --- |
| Important |
| If the hardened repository is assigned the VMware backup proxy role, you must also run through the Edit Proxy wizard to install additional components required for the proxy role. For more information, see [Editing VMware Backup Proxy Settings](backup_proxy_edit.md). |


