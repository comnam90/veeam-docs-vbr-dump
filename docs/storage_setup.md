---
title: "Configuring Storage Systems"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_setup.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Configuring Storage Systems


Before you start working with storage systems in Veeam Backup & Replication, you must configure the infrastructure. For more information on the required components and how to add them, see [Infrastructure Overview](storage_infrastructure.md).

Types of Storage Systems

Veeam Backup & Replication works with two types of storage systems:

* Built-in storage systems.

Storage systems whose integration is fully developed by Veeam and built into Veeam Backup & Replication. For more information, see [Built-In Storage Systems](storage_configure_add_storage.md).

* Universal storage API integrated systems.

Storage systems whose integration is developed by vendors using the Veeam Universal Storage API framework. These systems require installing a storage system plug-in. For more information, see [Universal Storage API Integrated Systems](universal_storage_integration_api.md).

Depending on the integration type you use, you can add different storage systems to your infrastructure. To learn which storage systems are supported for different types of integration, see [System Requirements](storage_system_requirements.md). Also, check the [requirements](storage_limitations.md) for a specific storage system before you add it to your backup infrastructure.

Working with Storage Systems

To start working with a storage system, you must add the storage system on which the backup data is hosted to the backup infrastructure. If you plan to work with a secondary storage array, you must add it to the backup infrastructure as well.

After you have added the storage system, you must [rescan](storage_rescan.md) it. You also need to rescan the system, for example, if you deleted or added snapshots not using Veeam Backup & Replication and want to update the information in Veeam Backup & Replication.

If you do not need the storage system anymore, you can [remove](storage_remove.md) it from the backup infrastructure.

In This Section

* [Adding Storage Systems](storage_configure_add_storage.md)
* [Rescanning Storage Systems](storage_rescan.md)
* [Removing Storage Systems](storage_remove.md)


