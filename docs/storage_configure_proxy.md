---
title: "Proxy Requirements (Storage Systems)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_configure_proxy.html"
last_updated: "12/3/2025"
product_version: "13.0.1.1071"
---

# Proxy Requirements (Storage Systems)


This section describes requirements for proxies used for storage integration.

General Requirements

* The proxy and the storage system must support the same IP version.
* For VMware integration

* You must assign to a Microsoft Windows or a Linux machine the role of a backup proxy. This can be a dedicated machine or backup server performing the role of the default backup proxy. For more information on the protocol support for different backup infrastructure components assigned the role of the backup proxy, see [Transport Modes](transport_modes.md#limitations).
* We recommend that you add only one proxy to one initiator group. Otherwise, you may encounter issues on proxies with the number of devices that correspond to storage snapshot clones. During the backup process, devices may be unintentionally created on all proxies added to the initiator group, for example, if two backup jobs that use proxies from the initiator group work simultaneously. The created devices may be accumulated.
* For backup from storage snapshots, the transport mode for VMware backup proxy must be set to Automatic selection or Direct storage access.
* For backup from storage snapshots, access to the production volumes or LUNs is not required. The backup proxy only accesses the snapshot/clone of the production datastore to read the data.

During backup, Veeam Backup & Replication creates a temporary snapshot of the production volume and then mounts it to the backup proxy. Therefore the backup proxy does not interact with the production volume or LUN, and mapping to the production volume is not required. For more information on how backup from storage snapshots works, see [Backup from Storage Snapshots](backup_from_storage_snapshots.md).

* For Linux-based backup proxy, to check compatibility with a storage system, see the system requirements provided by the storage system vendor.

* [For Veeam Agent and NAS integration] Check requirements for the general-purpose backup proxy. For more information, see the [General Purpose-Backup Proxy](backup_proxy_general.md) section in the Veeam Backup & Replication User Guide.
* If you want to configure multipathing (MPIO) feature for backup from storage snapshots, check the following:

* [For Windows-based backup proxies] The Multipath I/O feature is enabled in the Windows Server Manager console. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features).
* [For Linux-based backup proxies] The multipath feature is configured on the proxy.
* All ports of one proxy are in the same host group or initiator group on the storage system.
* [For iSCSI] The necessary iSCSI targets are connected and multiple iSCSI sessions are established from the backup proxy to the storage system.
* [For Fibre Channel] Zoning and masking on the FC switches and storage are configured.

iSCSI Protocol

* [For Windows-based backup proxies] The proxy must have a Microsoft iSCSI Software initiator enabled.
* [For Linux-based backup proxies deployed from Veeam Infrastructure Appliance ISO] [When deploying a proxy from ISO](linux_infrastructure_appliance_install.md), select the Veeam Infrastructure Appliance (with iSCSI & NVMe/TCP) option.
* [For Linux-based backup proxies] The proxy must have an Open-iSCSI Software initiator enabled. For proxies deployed from Veeam Infrastructure Appliance ISO, the initiator is already enabled.
* For the majority of storage systems, Veeam Backup & Replication requests the storage system to create the iSCSI host automatically if Veeam Backup & Replication cannot find the host with the proxy server initiator IQN. If the host was not created, consult the storage-specific documentation for additional steps.

If the proxy is deployed [using Veeam Infrastructure Appliance](linux_infrastructure.md), you can find the IQN on the overview page in the Veeam Host Management console. For more information on how to access the console, see [Accessing Veeam Host Management Console](hmc_access.md).

* iSCSI traffic between the proxy and storage system must be allowed.

|  |
| --- |
| Note |
| Consider the following:   * For storage rescan, Veeam Backup & Replication uses its own Veeam iSCSI initiator. The requirements for iSCSI initiators depend on the type of proxy used:  * For Linux-based proxies deployed from Veeam Infrastructure Appliance ISO or for the Linux-based backup server that acts as a proxy, you must enable an Open-iSCSI Software initiator (iscsid). * For Microsoft Windows-based and Linux-based proxies that are not deployed from Veeam Infrastructure Appliance ISO, the Microsoft iSCSI Software initiator and Open-iSCSI do not need to be enabled.  * For backup from storage snapshots, you must enable the Microsoft iSCSI Software initiator and Open-iSCSI. |

SMB (CIFS) Protocol

SMB (CIFS) traffic between the proxy and storage system must be allowed.

Fibre Channel Protocol

* The proxy must have a Fibre channel adapter installed and must have access to the storage system over Fibre Channel fabric.
* To let Veeam Backup & Replication present LUNs of snapshots to the proxy, you must register the proxy with a WWN ID on the storage system.
* Fibre Channel devices must be properly installed on the proxy. For example, see the vendor documentation and check that the proxy OS and the Fibre Channel adapter are compatible. Also, check that the WWN ID of the proxy is properly zoned on the Fibre Channel switch.
* We recommend configuring the proxy on a physical machine.

NFS Protocol

* NFS traffic between the backup proxy and storage system must be allowed.
* [For Linux-based backup proxies] The backup proxy must have an NFS client enabled.

NVMe-oF Protocol

* The NVMe-oF protocol can be used only with Linux-based backup proxies.

* [For Linux-based backup proxies deployed from Veeam Infrastructure Appliance ISO] [When deploying a proxy from ISO](linux_infrastructure_appliance_install.md), select the Veeam Infrastructure Appliance (with iSCSI & NVMe/TCP) option.

* The NVMe-cli tool must be installed on the proxy. For proxies deployed from Veeam Infrastructure Appliance ISO, the tool is already installed.
* For Veeam Backup & Replication to present NVMe namespaces of snapshots to the proxy, you must register the proxy with an NVMe Qualified Name (NQN) on the storage system.

If the proxy is deployed [using Veeam Infrastructure Appliance](linux_infrastructure.md), you can find the NQN on the overview page in the Veeam Host Management console. For more information on how to access the console, see [Accessing Veeam Host Management Console](hmc_access.md).

* For proxies deployed from Veeam Infrastructure Appliance ISO, the NVMe-TCP technology is supported.

For other proxies, the following technologies are supported: NVMe-RDMA, NVMe-FC and NVMe-TCP.

* For the NVMe-RDMA technology, the proxy must have an NVMe-RDMA adapter.
* The following applies to NVMe-FC:

* The proxy must have an NVMe-FC adapter installed and also access to the storage system over Fibre Channel fabric.
* Install NVMe-FC devices on the proxy must be installed according to the vendor documentation. Ensure that the proxy operating system and the Fibre Channel adapter are compatible. Also, check that the WWN ID of the proxy is properly zoned on the Fibre Channel switch.


