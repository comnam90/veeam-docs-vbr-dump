---
title: "New-VBRStorageProtocolPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrstorageprotocolpolicy.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# New-VBRStorageProtocolPolicy

In this article

Short Description

Creates protocol policies for storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRStorageProtocolPolicy [-iSCSI] [-FibreChannel] [-NFS] [-SMB] [-NVMe] [-CreateExportRulesAutomatically]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a protocol policy for storage systems.

You can select a protocol over which you want to work with the storage system: iSCSI, FibreChannel, NFS or SMB.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| iSCSI | Defines that the storage works over the iSCSI protocol. | SwitchParameter | False | Named | False |
| FibreChannel | Defines that the storage works over the FibreChannel protocol. | SwitchParameter | False | Named | False |
| NFS | Defines that the storage works over the NFS protocol. | SwitchParameter | False | Named | False |
| SMB | Defines that the storage works over the SMB protocol. | SwitchParameter | False | Named | False |
| NVMe | Defines that the storage works over the NVMe protocol. | SwitchParameter | False | Named | False |
| CreateExportRulesAutomatically | For SMB and NFS protocols.  Defines whether to automatically create export rules on the storage system during storage rescan, backup and restore operations. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRStorageProtocolPolicy](vbrstorageprotocolpolicy.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating iSCSI Protocol Policy

|  |  |
| --- | --- |
| This command creates an iSCSI protocol policy. Save it to the $protocol variable for future needs.  |  | | --- | | $protocol = New-VBRStorageProtocolPolicy -iSCSI | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Changing iSCSI Protocol for HPE 3PAR StoreServ Storage

|  |  |
| --- | --- |
| This example shows how to change the protocol over which the HPE 3PAR StoreServ storage is connected.  |  | | --- | | $storage = Get-HP3Storage -Name "HPE 3PAR StoreServ"  $protocol = New-VBRStorageProtocolPolicy -iSCSI  Set-HP3Storage -Host $storage -ProtocolPolicy $protocol |  Perform the following steps:   1. Run the [Get-HP3Storage](get-hp3storage.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the New-VBRStorageProtocolPolicy cmdlet. Provide the iSCSI parameter. Save the result to the $protocol variable. 3. Run the [Set-HP3Storage](set-hp3storage.md) cmdlet. Set the $storage variable as the Host parameter value. Set the $protocol variable as the ProtocolPolicy parameter value. |

Related commands

* [Get-HP3Storage](get-hp3storage.md)
* [Set-HP3Storage](set-hp3storage.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
