---
title: "Ports (Storage Systems)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ports.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Ports (Storage Systems)


On backup infrastructure components, Veeam Backup & Replication automatically creates firewall rules for the required ports. These rules allow communication between the components. You can find the full list of the ports below.

* [Dell Unity XT, Unity Storage](#dell_unity)

* [Dell PowerScale (formerly Isilon) Storage](#dell_isilon)

* [HPE 3PAR StoreServ Storage](#3par)
* [HPE Alletra Storage MP B10000, Alletra 9000, Primera Storage](#hpe_primera)
* [HPE Alletra 5000, Alletra 6000, Nimble Storage](#nimble)
* [Lenovo ThinkSystem DM/DG Series Storage](#lenovo_thinksystem)
* [NetApp ONTAP Storage](#netapp)
* [Nutanix Files Storage](#nutanix_files_storage)
* [Universal Storage API Integrated System](#usais)

Dell Unity XT, Unity Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Dell Unity XT/Unity storage system | TCP | 443 | Default port used for communication with Dell Unity XT/Unity over HTTPS and sending REST API calls. |
| Backup proxy | Dell Unity XT/Unity storage system | TCP | 3260 | Default iSCSI target port. |
| TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |

Dell PowerScale (Formerly Isilon) Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Dell PowerScale storage system | TCP | 8080 | Default port used for communication with Dell PowerScale over HTTPS and sending REST API calls. |
| Backup proxy | Dell PowerScale storage system | TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |

HPE 3PAR StoreServ Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | HPE 3PAR StoreServ storage system | TCP | 8008 | Default port used for communication with HPE 3PAR StoreServ over HTTP. |
| TCP | 8080 | Default port used for communication with HPE 3PAR StoreServ over HTTPS. |
| TCP | 22 | Default command port used for communication with HPE 3PAR StoreServ over SSH. |
| Backup proxy | HPE 3PAR StoreServ storage system | TCP | 3260 | Default iSCSI target port. |

HPE Alletra Storage MP B10000, Alletra 9000, Primera Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | HPE Alletra Storage MP B10000/Alletra 9000/Primera storage system | TCP | 443 | Default port used for communication with HPE Alletra Storage MP B10000/Alletra 9000/Primera over HTTPS. |
| TCP | 22 | Default command port used for communication with HPE Alletra Storage MP B10000/Alletra 9000/Primera over SSH. |
| Backup proxy | HPE Alletra Storage MP B10000/Alletra 9000/Primera storage system | TCP | 3260 | Default iSCSI target port. |
| HPE Alletra Storage MP B10000/Alletra 9000 | TCP | 4420, 8009 | Default NVMe-oF ports. |

HPE Alletra 5000, Alletra 6000, Nimble Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | HPE Alletra 5000/Alletra 6000/Nimble storage system | TCP | 5392 | Default command port used for communication with HPE Alletra 5000/Alletra 6000/Nimble. |
| Backup proxy | HPE Alletra 5000/Alletra 6000/Nimble storage system | TCP | 3260 | Default iSCSI target port. |

Lenovo ThinkSystem DM/DG Series Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Lenovo ThinkSystem DM/DG Series storage system | TCP | 80 | Default command port used for communication with Lenovo ThinkSystem DM/DG Series over HTTP. |
| TCP | 443 | Default command port used for communication with Lenovo ThinkSystem DM/DG Series over HTTPS. |
| Backup proxy | Lenovo ThinkSystem DM/DG Series storage system | TCP, UDP | 111, 2049, 635 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |
| TCP | 3260 | Default iSCSI target port. |

NetApp ONTAP Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | NetApp ONTAP storage system | TCP | 80 | Default command port used for communication with NetApp ONTAP over HTTP. |
| TCP | 443 | Default command port used for communication with NetApp ONTAP over HTTPS. |
| Backup proxy | NetApp ONTAP storage system | TCP, UDP | 111, 2049, 635 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |
| TCP | 3260 | Default iSCSI target port. |

Nutanix Files Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Nutanix Files storage system | TCP | 9440 | Default port used for communication with Nutanix Files and sending REST API calls. |
| Backup proxy | Nutanix Files storage system | TCP, UDP | 111, 2049, 20048 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |

Universal Storage API Integrated System

The following tables describe network ports that must be opened to ensure proper communication with Universal Storage API integrated systems:

* [DataCore SANsymphony](#DataCore)
* [Dell SC Series](#DellEMC)
* [Dell PowerMax](#dell_powermax)
* [Dell PowerStore](#dell_powerstore)
* [Fujitsu ETERNUS DX/AF](#fujitsu)

* [Hitachi VSP/VSP One Block](#vsp)
* [IBM FlashSystem (formerly Spectrum Virtualize) Storage](#ibm)

* [INFINIDAT InfiniBox](#infinidat)

* [NEC Storage M Series](#necm)
* [NetApp SolidFire/HCI](#solidfire)
* [Pure Storage FlashArray](#pure)
* [Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)](#WesternDigital)

DataCore SANsymphony

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | DataCore SANsymphony storage system | TCP | 443 | Default command port used for communication with DataCore SANsymphony over HTTPS. |
| Backup proxy | DataCore SANsymphony storage system | TCP | 3260 | Default iSCSI target port. |

Dell SC Series

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Dell SC Series storage system | TCP | 3033 | Default command port used for communication with Dell SC Series over HTTPS. |
| Backup proxy | Dell SC Series storage system | TCP | 3260 | Default iSCSI target port. |

Dell PowerMax

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Dell PowerMax storage system | TCP | 8443 | Default command port used for communication with Dell PowerMax over HTTPS. |
| Backup proxy | Dell PowerMax storage system | TCP | 3260 | Default iSCSI target port. |

Dell PowerStore

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Dell PowerStore storage system | TCP | 443 | Default command port used for communication with Dell PowerStore over HTTPS. |
| Backup proxy | Dell PowerStore storage system | TCP | 3260 | Default iSCSI target port. |

Fujitsu ETERNUS DX/AF

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Fujitsu ETERNUS DX/AF storage system | TCP | 22 | Default command port used for communication with Fujitsu ETERNUS DX/AF over SSH. |
| Backup proxy | Fujitsu ETERNUS DX/AF storage system | TCP | 3260 | Default iSCSI target port. |

Hitachi VSP/VSP One Block

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Hitachi VSP/VSP One Block storage system | TCP | 443 | Default command port used for communication with Hitachi VSP/VSP One Block over HTTPS. |
| Backup proxy | Hitachi VSP/VSP One Block storage system | TCP | 3260 | Default iSCSI target port. |

IBM FlashSystem (formerly Spectrum Virtualize) Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | IBM FlashSystem storage system | TCP | 22 | Default command port used for communication with IBM FlashSystem over SSH. |
| Backup proxy | IBM FlashSystem storage system | TCP | 3260 | Default iSCSI target port. |

INFINIDAT InfiniBox

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | INFINIDAT InfiniBox storage system | TCP | 443 | Default command port used for communication with INFINIDAT InfiniBox over HTTPS. |
| Backup proxy | INFINIDAT InfiniBox storage system | TCP | 3260 | Default iSCSI target port. |

NEC Storage M Series

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | NEC Storage M Series storage system | TCP | 22 | Default command port used for communication with NEC Storage M Series over SSH. |
| Backup proxy | NEC Storage M Series storage system | TCP | 3260 | Default iSCSI target port. |

NetApp SolidFire/HCI

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | NetApp SolidFire/HCI storage system | TCP | 443 | Default command port used for communication with NetApp SolidFire/HCI over HTTPS. |
| Backup proxy | NetApp SolidFire/HCI storage system | TCP | 3260 | Default iSCSI target port. |

Pure Storage FlashArray

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Pure Storage FlashArray system | TCP | 443 | Default command port used for communication with Pure Storage FlashArray over HTTPS. |
| Backup proxy | Pure Storage FlashArray system | TCP | 3260 | Default iSCSI target port. |
| Pure Storage FlashArray system | TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |

Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Tintri IntelliFlash system | TCP | 443 | Default command port used for communication with Tintri IntelliFlash over HTTPS. |
| Backup proxy | Tintri IntelliFlash system | TCP | 3260 | Default iSCSI target port. |
| Tintri IntelliFlash system | TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |


