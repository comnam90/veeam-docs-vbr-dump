---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_copy_before_you_begin.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create a VM copy job, check the following prerequisites:

* Backup infrastructure components that will take part in the VM copying process must be added to the backup infrastructure and properly configured. These include the source ESXi host and server or backup repository on which you plan to store the VM copy.
* The target storage device must have enough free space to store created VM copies. To receive alerts about low space on the storage device, configure global notification settings. For more information, see [Specifying Global Notification Settings](global_notifications.md).
* If you plan to use pre-freeze and post-thaw scripts, you must create scripts before you configure the VM copy job.

Consider the following limitations:

* Due to Microsoft limitations, you cannot use Microsoft Entra ID (formerly Azure Active Directory) credentials to perform application-aware processing on VMs running Microsoft Windows 10 (or later).
* If you use tags to categorize virtual infrastructure objects, check limitations for VM tags. For more information, see [VM Tags](vm_tags.md).


