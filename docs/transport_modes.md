---
title: "Transport Modes"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/transport_modes.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Transport Modes


A transport mode is a method that is used by the [Veeam Data Mover](veeam_transport_service.md) to retrieve VM data from the source and write VM data to the target. Job efficiency and time required for job completion greatly depend on the transport mode.

For data retrieval, Veeam Backup & Replication offers the following modes (starting from the most efficient):

* [Direct storage access](direct_storage_access.md)
* [Virtual Appliance (HotAdd)](virtual_appliance.md)
* [Network](network_mode.md)

The Veeam Data Mover responsible for data retrieval runs on a VMware backup proxy. The transport mode can be defined in the settings of the VMware backup proxy that performs the job.

When you configure VMware backup proxy settings, you can manually select a transport mode, or let Veeam Backup & Replication select the most appropriate mode automatically. If you use automatic mode selection, Veeam Backup & Replication will scan VMware backup proxy configuration and its connection to the VMware vSphere infrastructure to choose the optimal transport mode. If several transport modes are available for the same VMware backup proxy, Veeam Backup & Replication will choose the mode in the following order: Direct storage access > Virtual appliance > Network.

The selected transport mode is used for data retrieval. For writing data to the target, Veeam Backup & Replication picks the transport mode automatically, based on the configuration of the VMware backup proxy and transport mode limitations.

Veeam Backup & Replication leverages VMware vStorage APIs for Data Protection (VADP) for all transport modes except for backup from storage snapshots, the direct NFS transport mode and the virtual appliance transport mode. VADP can be used for VMware vSphere starting from version 4.

Applicability and efficiency of each transport mode primarily depends on the type of datastore used by the source host — local or shared, and on the VMware backup proxy type — physical or virtual. The following table shows recommendations for installing the VMware backup proxy, depending on the storage type and desired transport mode.

| Production Storage Type | Direct Storage Access | Virtual Appliance | Network Mode |
| --- | --- | --- | --- |
| Fibre Channel (FC) SAN | Install a VMware backup proxy on a physical server with a direct FC access to the SAN. | Install a VMware backup proxy on a VM running on an ESXi host connected to the storage device. | This mode is not recommended on 1 Gb Ethernet but works well with 10 Gb Ethernet.  Install a VMware backup proxy on any machine on the storage network. |
| iSCSI SAN | Install a VMware backup proxy on a physical or virtual machine. |
| NFS Storage |
| Shared SAS | Install a VMware backup proxy on a physical server with a direct SAS access to the SAN. |
| vSAN | Not supported. | Install a VMware backup proxy on a VM running on an ESXi host connected to the VSAN storage device. |
| vVol | Install a VMware backup proxy on a VM running on an ESXi host connected to the vVol storage. |
| Local Storage | Install a VMware backup proxy on a VM on every ESXi host. |

|  |
| --- |
| Note |
| If you use VMware Cloud on AWS, the only available transport mode is Virtual appliance. We recommend you install a VMware backup proxy on a VM running on an ESXi host connected to the VSAN storage device. |

Transport Mode Limitations

The transport mode limitations are defined by the backup proxy configuration. The following table describes transport mode availability and protocol support for different backup infrastructure components assigned the role of the backup proxy in VMware vSphere environments and storage system integration.

| Component Used as Backup Proxy | Direct Storage Access | | | Virtual Appliance | Network Mode |
| --- | --- | --- | --- | --- | --- |
| Direct SAN Access1 | Direct NFS Access | Storage Integration1 |
| Veeam Software Appliance | ✕ | ✕ | ✕ | ✕ | ✓ |
| Veeam Infrastructure Appliance2 | ✕ | ✓ | NFS | ✓ | ✓ |
| Veeam Infrastructure Appliance with iSCSI and NVMe/TCP2 | ✕ | ✓ | iSCSI, NFS, NVMe-TCP | ✓ | ✓ |
| Veeam Hardened Repository | ✕ | ✕ | ✕ | ✕ | ✓ |
| Windows-based backup server | ✓ | ✓ | iSCSI, FC, NFS | ✓ | ✓ |
| Microsoft Windows server | ✓ | ✓ | iSCSI, FC, NFS | ✓ | ✓ |
| Linux server added with persistent credentials | ✓ | ✓ | iSCSI, FC, NFS, NVMe-FC, NVMe-TCP, NVMe-RDMA | ✓ | ✓ |
| Linux server added with single-use credentials as Hardened Repository | ✕ | ✕ | ✕ | ✕ | ✓ |

1 Manual configuration is required in some cases. For more information, see [Direct SAN Access](direct_san_access.md) and [Proxy Requirements (Storage Systems)](storage_configure_proxy.md).

2 These backup infrastructure components may support additional transport modes and block protocols if configured manually using root access permissions.


