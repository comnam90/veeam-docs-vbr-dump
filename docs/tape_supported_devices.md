---
title: "Supported Devices and Configuration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_supported_devices.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# Supported Devices and Configuration


Veeam Backup & Replication supports Linear Tape-Open (LTO) and IBM 3592 (Jaguar) tape libraries:

* Physical libraries, standalone drives and virtual tape libraries.
* Partitions of the physical or virtual tape libraries presented to the Veeam backup server.

For more information on supported devices, see [System Requirements](system_requirements.md#tape).

Limitations

When configuring your tape environment, consider the following limitations:

* VMware does not support tape drives connected directly to ESXi 5.x and later. For more information, see [this VMware KB article](https://knowledge.broadcom.com/external/article/310914/configuring-vendorsupported-tape-drives.html).

VMware does not support tape drives connected via Fibre Channel NPIV (N-port ID virtualization). For more information, see [VMware Docs](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/vsphere-storage-8-0/using-esxi-with-fibre-channel-san/using-fibre-channel-npiv-with-vsphere-virtual-machines.html).

Veeam Backup & Replication will potentially work with such a configuration, but if there is a hardware-related issue, Veeam Support will not provide help to solve it. This functionality is vendor-supported.

* For the socket-based licensing model, IBM 3592 tape library support requires Enterprise Plus edition of Veeam Backup & Replication.

* Within a library partition, only one generation of LTO drives or IBM 3592 drives is supported.
* You cannot combine tapes from LTO drives and IBM 3592 drives in one media pool.
* LTO tape versions that are released after Veeam Backup & Replication 13 reaches end-of-fix are not supported.

Affecting 3rd Party Tape Solutions

Veeam Backup & Replication does not support sharing tape devices with other Veeam backup servers, with different tape servers of one Veeam Backup & Replication installation, or with 3rd party tape-recording software. If you plan to run both Veeam Backup & Replication and 3rd party tape-recording software (for example, in your evaluation lab), consider that Veeam Backup & Replication by default will periodically lock the drive to perform rescan, preventing other software from recording.

To share a tape device, configure a partition of the tape library that will be used only by Veeam Backup & Replication.

Consider the following limitations:

* Do not connect partitions presented to the 3rd party tape software to a Veeam tape server.
* Do not install any 3rd party tape-recording software or software components on Veeam tape server.

Driver Installation Mode

Veeam Backup & Replication supports both exclusive and non-exclusive driver installation.

|  |
| --- |
| Note |
| If you use standalone tape drives, it is recommended to install drivers in non-exclusive mode. |

Path Failover

Veeam Backup & Replication supports path failover for tape devices with multiple drives that manage multiple paths over multiple SANs.

|  |
| --- |
| Note |
| Veeam does not supply MPIO drivers. To get proper MPIO drivers, request them from the tape device vendor. |

Industry Format

Veeam Backup & Replication uses the MTF (Microsoft Tape Format) industry format to write data to tape.

Supported Connection Types

You can connect the tape device directly or remotely.

* Direct connection:

+ Fibre Channel (FC)
+ Serial Attached SCSI (SAS)
+ SCSI

* Remote connection:

+ iSCSI
+ Switched FC fabric

Data Block Size

Drives use hardware dependent block sizes to read/write the tape data. Generally, the drives support a range of block sizes and report this range to Veeam Backup & Replication.

If you use a tape library with multiple drives or you use multiple standalone drives, Veeam Backup & Replication uses a unified block size to write data to tapes. 256k data block size is used if all drives can support it. If any drive can support only a smaller block size, for example, 64k, then Veeam Backup & Replication uses the largest block supported by all drives. To understand block sizes supported by drives, Veeam Backup & Replication collects the block size ranges reported by each drive and compares them. Note that the reported range is additionally limited by storage controllers settings used in your infrastructure. You can check the resulting range of block sizes supported by Veeam Backup & Replication for a particular drive in the Drives properties. For more information, see [Tape Drives](working_with_drives.md).

|  |
| --- |
| Note |
| If you connect the tape devices using HBA, Veeam Backup & Replication uses the block size configured for the HBA. |

The block size is unified for:

* All drives in one library (if the drives support different block sizes).
* All standalone drives connected to one tape server.

To read data from tape, Veeam Backup & Replication requires that the tape is written with the block size from the supported range (shown in the drive properties).

Consider the block size range when working with the following tapes:

* Tapes with Veeam backups written by another tape library.
* Tapes with Veeam backups written on another tape server.
* Tapes written with other data transfer configuration settings.
* Tapes written on a 3rd party device.

|  |
| --- |
| Important |
| You can restore from tapes written with block size that match the block size range set for the tape device. |

Unknown Medium Changers

Veeam supports medium changers that have no Microsoft Windows drivers available. Make sure that such device is recognized as an unknown medium changer in the Microsoft Device Manager list.

It is recommended that you use tape devices with original equipment manufacturer (OEM) drivers.


