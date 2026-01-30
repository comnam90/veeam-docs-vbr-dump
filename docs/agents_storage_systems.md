---
title: "Storage Snapshots Support"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_storage_systems.html"
last_updated: "8/6/2025"
product_version: "13.0.1.1071"
---

# Storage Snapshots Support


You can use Veeam Backup & Replication and Veeam Agent for Microsoft Windows operating in the managed mode (within the Veeam Agent management scenario) to create backups from native storage snapshots.

Native storage snapshots allow the following:

* Veeam Backup & Replication to use backup proxy servers to process storage systems.
* Veeam Agent to use hardware Volume Shadow Copy Service (VSS) provider and capabilities of native snapshots that are created on production storage systems to create backups.

This approach results in much less load on protected servers compared to the regular backup scenario that uses software VSS provider.

For general information about backup jobs that use storage snapshots as a data source, see [Storage System Snapshot Integration](storage_integration.md).

Getting Started

Before you configure a Veeam Agent backup job that will use a storage system snapshot as a data source, you must complete the following steps:

1. Configure the backup infrastructure to create backups from native storage snapshots. To learn more, see [Backup Infrastructure for Storage Integration](storage_setup.md).

Keep in mind that you must allow your storage to process Veeam Agent backups. To do this, select the Block storage for Microsoft Windows servers check box at the Name step of the New Storage wizard, then specify options for accessing the storage system at the Agent Access step of the wizard. To learn more, see [Adding Storage Systems](storage_configure_add_storage.md).

Veeam Agent for Microsoft Windows allows you to create backups from native snapshots with hardware VSS provider only. For the list of supported storage systems, see [Veeam Agent Integration](agent_integration.md).

1. Add a Microsoft Windows computer to the inventory and deploy Veeam Agent for Microsoft Windows on this computer using the Veeam Backup & Replication console. To learn more, see [Creating Protection Groups](protection_group_add.md).

Considerations and Limitations

Before you create a Veeam Agent backup from a storage system snapshot, check the following prerequisites:

* The backup proxy and the Veeam Agent computer must run Microsoft Windows Server OS versions. The backup proxy cannot run the OS version that is earlier than the Veeam Agent computer OS version.
* You must use the following product editions:

* The Standard, Enterprise, or Enterprise Plus edition of Veeam Backup & Replication on the backup server with the backup proxy role.

* The Server edition of Veeam Agent for Microsoft Windows on the Veeam Agent computer.

You can check product editions in the License Information window of the Veeam Backup & Replication backup console. To learn more, see [Viewing License Information](license_view.md).

* At least one storage logical unit number (LUN) must be mapped to the Veeam Agent computer.

* At least one backup proxy must have access to all LUNs.

* You must use iSCSI or Fibre Channel protocol for your storage system:

* You must use iSCSI or Fibre Channel protocol to connect LUNs to Veeam Agent computer and backup proxy to your storage system.
* If you plan to use the iSCSI Protocol, the backup proxy and the Veeam Agent computer must have a Microsoft iSCSI Software initiator enabled.
* If you plan to use the Fibre Channel Protocol, the backup proxy and the Veeam Agent computer must have a Fibre channel adapter installed and must have access to the storage system over Fibre Channel fabric.

* If a Veeam Agent computer has a storage system with disks that use the GUID Partition Table (GPT) as a partitioning scheme, each disk must contain a Microsoft Reserved (MSR) partition.

In addition to [general limitations](storage_limitations_general.md), consider the following limitations for Veeam Agent backups from storage snapshots:

* You cannot create file-level backup from a storage snapshot.

* If the Storage Replica feature is installed on the Veeam Agent computer, you cannot back up this computer using the hardware VSS provider. If you want to add this computer to the backup scope, you must allow Veeam Backup & Replication to fail over to the regular backup scenario that uses software VSS provider. To learn more, see [Integration Settings](agent_job_advanced_integration.md). To learn more about Storage Replica, see [Microsoft documentation](https://docs.microsoft.com/en-us/windows-server/storage/storage-replica/storage-replica-overview).

* The backup proxy and the Veeam Agent computer you want to back up cannot be the same computer.
* You cannot back up the following objects using the hardware VSS provider:

* Volumes allocated to the RDM disk
* Storage spaces

With volumes allocated to RDM disks or storage spaces in the backup scope, Veeam Backup & Replication will fail over to the regular backup scenario even if failover is not allowed in [storage integration settings](agent_job_advanced_integration.md).

* If your Veeam Agent computer has a disk that contains the storage spaces protective partition, you cannot back up volumes allocated to this disk using the hardware VSS provider. To back up such volumes, you must allow Veeam Backup & Replication to fail over to the regular backup scenario that uses software VSS provider. To learn more about failover, see [Integration Settings](agent_job_advanced_integration.md).

* Volumes greater than 64 TB are supported with limitations. To learn more, see [Storage Snapshots on Volumes Greater than 64 TB](agents_storage_snapshots_great.md).
* BitLocker encrypted volumes are supported with limitations. To learn more, see [Storage Snapshots on BitLocker Encrypted Volumes](agents_storage_snapshots_encrypted.md).

In This Section

* [Backup from Storage Snapshots](agents_storage_snapshots_hiw.md)
* [Storage Snapshots on Volumes Greater than 64 TB](agents_storage_snapshots_great.md)
* [Storage Snapshots on BitLocker Encrypted Volumes](agents_storage_snapshots_encrypted.md)


