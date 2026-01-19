---
title: "Reinstalling Veeam Infrastructure Appliance with ISO"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/linux_infrastructure_appliance_reinstall.html"
last_updated: "1/19/2026"
product_version: "13.0.1.1071"
---

# Reinstalling Veeam Infrastructure Appliance with ISO


To recover the operating system, you can reinstall Veeam Infrastructure Appliance on a backup infrastructure component.

|  |
| --- |
| Note |
| If you replace the operating system drive, it must be the smallest SSD or NVMe drive on the system. If this requirement is not met, data loss will occur. |

To reinstall Veeam Infrastructure Appliance, perform the following steps:

1. Boot from the JeOS ISO file.
2. In the installation menu, select the product. Then, select Reinstall.
3. When the installer is loaded, confirm the operation.
4. After the installation is complete, do the following:

1. Select Reboot System or wait for the system to reboot automatically.
2. After the system reboots, complete the Initial Configuration wizard as described in the [Installing Veeam Infrastructure Appliance with ISO](linux_infrastructure_appliance_install.md) section.


