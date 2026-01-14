---
title: "System Requirements (Storage Systems)"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_system_requirements.html"
last_updated: "9/23/2025"
product_version: "13.0.1.1071"
---

# System Requirements (Storage Systems)

In this article

Veeam Backup & Replication provides different types of snapshot integrations and these integrations support different storage systems. For details, see the following table.

|  |
| --- |
| NOTE |
| [For VMware integration] You may encounter scenarios when Veeam Backup & Replication and the storage system support different versions of the virtual platform. In such cases, we recommend using versions supported by the storage system. If other versions are used, Veeam support will assist only with issues unrelated to version compatibility. |

|  | Microsoft Windows-based Backup Server | | Linux-based Backup Server | |
| --- | --- | --- | --- | --- |
| NAS Integration | VMware and Agent Integrations | NAS Integration | VMware and Agent Integrations |
| Built-In Storage Systems | | | | |
| Cisco HyperFlex HX-Series | ✕ | * VMware integration only (experimental, see [this Veeam KB article](https://www.veeam.com/kb2976)) * NFS connectivity only * HyperFlex 5.0 (2x) or later (Backup from Storage Snapshots, Full Integration mode) * Basic authentication is not supported for SSO users in HyperFlex | ✕ | * VMware integration only (experimental, see [this Veeam KB article](https://www.veeam.com/kb2976)) * NFS connectivity only * HyperFlex 5.0 (2x) or later (Backup from Storage Snapshots, Full Integration mode) * Basic authentication is not supported for SSO users in HyperFlex |
| Dell PowerScale (formerly Isilon) | * Filer integration for NAS backup functionality * NFS or SMB (CIFS) connectivity * OneFS 8.1.2 to 9.11 | ✕ | * Filer integration for NAS backup functionality * NFS or SMB (CIFS) connectivity * OneFS 8.1.2 to 9.11 | ✕ |
| Dell Unity (XT) | ✕ | * NFS, Fibre Channel (FC) or iSCSI connectivity  * Dell Unity XT/Unity OE versions 5.0 to 5.5 | ✕ | * NFS, Fibre Channel (FC) or iSCSI connectivity  * Dell Unity XT/Unity OE versions 5.0 to 5.5 |
| Fujitsu ETERNUS HX/AX | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported | * NFS, Fibre Channel or iSCSI connectivity * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.10 to 9.17.1 * ONTAP 7-mode is not supported | ✕ |
| HPE 3PAR StoreServ | ✕ | * Fibre Channel (FC) or iSCSI connectivity * 3PAR OS versions 3.2.2 up to 3.3.2 * WSAPI 1.5 and later  * iSCSI VLAN tags are supported | ✕ | * Fibre Channel (FC) or iSCSI connectivity * 3PAR OS versions 3.2.2 up to 3.3.2 * WSAPI 1.5 and later  * iSCSI VLAN tags are supported |
| HPE Alletra 5000/6000 | ✕ | * Fibre Channel (FC) or iSCSI connectivity * OS version 6.1 | ✕ | * Fibre Channel (FC) or iSCSI connectivity * OS version 6.1 |
| HPE Alletra 9000 | ✕ | * Fibre Channel (FC), iSCSI or NVMe-oF connectivity * OS version 9.3 or later | ✕ | * Fibre Channel (FC), iSCSI or NVMe-oF connectivity * OS version 9.3 or later |
| HPE Alletra Storage MP B10000 | ✕ | * Fibre Channel (FC), iSCSI or NVMe-oF connectivity   iSCSI is supported starting from OS version 10.3.   * OS version 10.2 or later | ✕ | * Fibre Channel (FC), iSCSI or NVMe-oF connectivity   iSCSI is supported starting from OS version 10.3.   * OS version 10.2 or later |
| HPE Nimble Storage AF-Series, | ✕ | * Fibre Channel (FC) or iSCSI connectivity * Nimble OS from 5.2 up to 6.1.2 | ✕ | * Fibre Channel (FC) or iSCSI connectivity * Nimble OS from 5.2 up to 6.1.2 |
| HPE Primera | ✕ | * Fibre Channel (FC) or iSCSI connectivity   iSCSI is supported starting starting from OS versions 4.3 or later.   * OS versions 4.x | ✕ | * Fibre Channel (FC) or iSCSI connectivity   iSCSI is supported starting starting from OS versions 4.3 or later.   * OS versions 4.x |
| Lenovo ThinkSystem DM/DG Series | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported | * NFS, Fibre Channel or iSCSI connectivity * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.10 to 9.17.1 * ONTAP 7-mode is not supported | ✕ |
| NetApp FAS/AFF/ASA, | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported * NetApp ASA r2 systems (ASA A1K, ASA A70, and ASA A90) are not supported | * NFS, Fibre Channel or iSCSI connectivity * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported * NetApp ASA r2 systems (ASA A1K, ASA A70, and ASA A90) are not supported. | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.10 to 9.17.1 * ONTAP 7-mode is not supported * NetApp ASA r2 systems (ASA A1K, ASA A70, and ASA A90) are not supported | ✕ |
| Nutanix Files | * Filer integration for NAS backup functionality * NFS or SMB (CIFS) connectivity * Nutanix File Server 3.8.1.3 to 5.2 | ✕ | * Filer integration for NAS backup functionality * NFS or SMB (CIFS) connectivity * Nutanix File Server 3.8.1.3 to 5.2 | ✕ |
| Universal Storage API Integrated Systems | | | | |
| DataCore SANsymphony | ✕ | * Fibre Channel (FC) or iSCSI connectivity  * DataCore SANsymphony 10.0 PSP12 or later | ✕ | ✕ |
| Dell PowerMax | ✕ | * Fibre Channel (FC) or iSCSI connectivity * Dell PowerMax/VMAX All Flash (PowerMax OS microcode 5978.711.711 or later 5978 family updates, and PowerMaxOS 10.1.0.0 or later) * Unisphere for PowerMax 9.2.1.6 or later   For information on supported PowerMax versions, see [this Veeam KB article](https://www.veeam.com/kb4200). | ✕ | ✕ |
| Dell PowerStore | ✕ | * Fibre Channel (FC) or iSCSI connectivity * Dell PowerStore (PowerStore OS 3.0 to 4.2) | ✕ | ✕ |
| Dell SC Series (formerly Compellent) | ✕ | * Fibre Channel (FC) or iSCSI connectivity  * Storage Center OS 7.4.2 or later * FluidFS volumes and Live Volumes are not supported | ✕ | ✕ |
| Fujitsu ETERNUS AF and DX Series | ✕ | * Fibre Channel (FC) or iSCSI connectivity * ETERNUS AF series: AF250 S2, AF650 S2, AF150 S3, AF250 S3, AF650 S3 * ETERNUS DX series: DX60 S4, DX100 S4, DX200 S4, DX500 S4, DX600 S4, DX8900 S4, DX60 S5, DX100 S5, DX200 S5, DX500 S5, DX600 S5, DX900 S5, DX600 S6, DX900 S6, DX8900 S6 * Storage firmware version:  * ETERNUS AF S2 and DX S4 series (except DX8900 S4): V10L88-1000 or later * ETERNUS AF S3 and DX S5 series, DX8900 S4: V11L30-5000 or later * ETERNUS DX S6 series: V12L10-0000 or later | ✕ | ✕ |
| Hitachi VSP/VSP One Block | ✕ | * Fibre Channel (FC) or iSCSI connectivity  * VSP E series (93-03-01-60/00 or later) * VSP F series (88-07-01-x0/00 or later) * VSP G series (88-07-01-x0/00 or later) * VSP 5100 and VSP 5500 (90-05-01-00/00 or later) * VSP 5200 and VSP 5600 (90-08-01-00/00 or later) * VSP One Block series (A3-03-01-x0/01 or later) | ✕ | * Fibre Channel (FC) or iSCSI connectivity  * VSP E series (93-03-01-60/00 or later) * VSP F series (88-07-01-x0/00 or later) * VSP G series (88-07-01-x0/00 or later) * VSP 5100 and VSP 5500 (90-05-01-00/00 or later) * VSP 5200 and VSP 5600 (90-08-01-00/00 or later) * VSP One Block series (A3-03-01-x0/01 or later) |
| IBM FlashSystem (formerly Spectrum Virtualize,  includes IBM StorWize and IBM SVC) | ✕ | * Fibre Channel (FC) or iSCSI connectivity * IBM Spectrum Virtualize OS version 8.4 or later * Policy-based replication relationships are not detected   You will not be able to select this feature for backup and snapshot orchestration with secondary storage arrays.   * Policy-based high availability (PBHA) configurations are not supported   Volumes covered by PBHA cannot be used for the storage integration feature. | ✕ | * Fibre Channel (FC) or iSCSI connectivity * IBM Spectrum Virtualize OS version 8.4 or later * Policy-based replication relationships are not detected   You will not be able to select this feature for backup and snapshot orchestration with secondary storage arrays.   * Policy-based high availability (PBHA) configurations are not supported   Volumes covered by PBHA cannot be used for the storage integration feature. |
| INFINIDAT Infinibox F-Series | ✕ | * NFS, Fibre Channel (FC) or iSCSI connectivity * InfiniBox 5.0 or later   Note: You must add to the backup infrastructure only one of the two InfiniBox storage arrays for which Active/Active Replication is configured, or exclude the replicating volumes on one of these arrays from rescan. For details on how to exclude volumes from rescan, see [Rescanning Storage Systems](storage_rescan.md). | ✕ | ✕ |
| NEC Storage M Series | ✕ | * Fibre Channel (FC) or iSCSI connectivity  * M120, M320, M320F, M520, M720, M720F (Storage Control Software revision 1234 or later) | ✕ | ✕ |
| NetApp SolidFire/HCI | ✕ | * iSCSI connectivity * Element OS version 10.0 or later | ✕ | ✕ |
| Pure Storage FlashArray | ✕ | * NFS, Fibre Channel (FC) or iSCSI connectivity * Purity 6.3 or later | ✕ | ✕ |
| Tintri IntelliFlash  (formerly Western Digital IntelliFlash, Tegile) | ✕ | * NFS, Fibre Channel (FC) or iSCSI connectivity * Tintri IntelliFlash 3.11 or later | ✕ | ✕ |

Related Topics

* [VMware Integration](vmware_integration.md)
* [NAS Integration](nas_integration.md)
* [Veeam Agent Integration](agent_integration.md)

Page updated 9/23/2025

Page content applies to build 13.0.1.1071
