---
title: "Protection Group for InterSystems IRIS Databases"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_protection_group_hiw.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Protection Group for InterSystems IRIS Databases


In Veeam Backup & Replication, computers that you want to protect with Veeam Plug-Ins are organized into protection groups. A protection group is a container in the Veeam Backup & Replication inventory aimed to combine protected computers of a specific type.

To start managing computers with InterSystems IRIS instances using Veeam Backup & Replication, you need to create a protection group for InterSystems IRIS ODB servers in the inventory and specify computers that you want to protect in the protection group settings. You can create one or more protection groups depending on the size and complexity of your infrastructure. Protection groups appear under the Physical Infrastructure node in the Inventory view of the Veeam Backup & Replication console.

Veeam Backup & Replication connects to discovered computers using an administrative account or a certificate specified in the protection group settings. To learn more, see [Creating Protection Group for InterSystems IRIS Databases](iris_protection_group_create.md).

After you create a protection group, Veeam Backup & Replication starts the rescan job to connect to computers added to the protection group and perform the required operations on these computers. To learn more, see [Rescan Job](iris_rescan_job.md).

Page updated 2026-07-24

