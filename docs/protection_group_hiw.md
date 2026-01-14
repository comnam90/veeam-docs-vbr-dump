---
title: "Protection Groups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protection_group_hiw.html"
last_updated: "5/7/2025"
product_version: "13.0.1.1071"
---

# Protection Groups

In this article

In Veeam Backup & Replication, computers that you want to protect with Veeam Plug-Ins are organized into protection groups. A protection group is a container in the Veeam Backup & Replication inventory aimed to combine protected computers of a specific type. For example, you can use a dedicated protection group for computers of the same type or computers running the same OS type to simplify management of such computers. You can also use a separate protection group for computers that you want to manage in a different way from other computers in your infrastructure.

To start managing Veeam Plug-Ins in Veeam Backup & Replication, you need to create a protection group in the inventory and specify computers that you want to protect with Veeam Plug-Ins in the protection group settings. You can create one or more protection groups depending on the size and complexity of your infrastructure. Protection groups appear under the Physical Infrastructure node in the Inventory view of the Veeam Backup & Replication console. To learn more, see [Working with Protection Groups](protection_group.md).

Protection groups allow you to automate deployment and management of Veeam Plug-Ins on computers in your infrastructure. When you configure a protection group, you can specify scheduling options for protected computers discovery and Veeam Plug-In deployment. You do not need to perform administrative tasks individually for every computer that you want to protect with Veeam Plug-In — Veeam Backup & Replication will perform the specified operations automatically upon the defined schedule.

Veeam Backup & Replication connects to discovered computers using credentials of the account specified in the protection group settings. You can specify a master account that Veeam Backup & Replication will use to connect to all computers added to the protection group or specify separate accounts to connect to specific computers in the protection group.

After you create a protection group, Veeam Backup & Replication starts the rescan job to connect to computers added to the protection group and perform the required operations on these computers. To learn more, see [Rescan Job](rescan_job.md).

Related Topics

* [Protection Group Types](protection_group_types.md)
* [Predefined Protection Groups](protection_group_default.md)

Related Tasks

[Creating Protection Groups](protection_group_create.md)

Page updated 5/7/2025

Page content applies to build 13.0.1.1071
