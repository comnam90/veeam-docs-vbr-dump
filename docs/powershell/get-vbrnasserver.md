---
title: "Get-VBRNASServer (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasserver.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNASServer (obsolete)


Short Description

Returns file shares that are added to the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all file shares that are added to the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Get-VBRNASServer  [<CommonParameters>] |

* Get file shares by the file shares name.

|  |
| --- |
| Get-VBRNASServer -Name <string[]>  [<CommonParameters>] |

* Get file shares by the file shares ID.

|  |
| --- |
| Get-VBRNASServer -Id <guid[]>  [<CommonParameters>] |

* Get file shares by the name of the enterprise NAS system storage on which they are residing.

|  |
| --- |
| Get-VBRNASServer -SANEntity <VBRSANEntity[]>  [<CommonParameters>] |

* Get file shares by the backup that protects these file shares.

|  |
| --- |
| Get-VBRNASServer [-Backup <VBRNASBackup>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of file shares that are added to the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of a file share. The cmdlet will return an array of file shares with the specified name. | String[] | True | Named | False |
| Id | Specifies an ID of a file share. The cmdlet will return an array of file shares with the specified ID. | Guid[] | True | Named | False |
| SANEntity | Specifies a name of an enterprise NAS system. The cmdlet will return an array of file shares residing on this NAS system. | Accepts the VBRSANEntity[] object. To create this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | False |
| Backup | Specifies a backup. The cmdlet will return an array of file shares protected with this backup. | Accepts the VBRNASBackup object. To create this object, run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASServer object that contains settings of file shares added to the Veeam Backup & Replication infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All File Shares

|  |  |
| --- | --- |
| This command gets all file shares added to the Veeam Backup & Replication infrastructure. The cmdlet output will contain settings of these file shares.  |  | | --- | | Get-VBRNASServer  Type                : SMB  Path                : \\WinSRV2049\Documents  AccessCredentials   :  ProcessingMode      : Direct  StorageSnapshotPath :  ProxyMode           : Automatic  SelectedProxyServer : {}  Id                  : 4916c13e-08bf-488f-ab1b-1624d02189c5  CacheRepository     : Veeam.Backup.Core.CBackupRepository    Type                : NFS  Path                : \\LinuxSRV2049\Reports  AccessCredentials   :  ProcessingMode      : Direct  StorageSnapshotPath :  ProxyMode           : Automatic  SelectedProxyServer : {}  Id                  : 678eafe4-ad76-4878-8230-561b4226333c  CacheRepository     : Veeam.Backup.Core.CBackupRepository | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting File Shares by Name

|  |  |
| --- | --- |
| This command gets the WinSRV2049\Documents file share. The cmdlet output will contain settings of these file shares.  |  | | --- | | Get-VBRNASServer -Name "\\WinSRV2049\Documents"  Type                : SMB  Path                : \\WinSRV2049\Documents  AccessCredentials   :  ProcessingMode      : Direct  StorageSnapshotPath :  ProxyMode           : Automatic  SelectedProxyServer : {}  Id                  : 4916c13e-08bf-488f-ab1b-1624d02189c5  CacheRepository     : Veeam.Backup.Core.CBackupRepository | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting File Share by ID

|  |  |
| --- | --- |
| This command gets file share by the file share ID. The cmdlet output will contain settings of these file shares.  |  | | --- | | Get-VBRNASServer -Id "678eafe4-ad76-4878-8230-561b4226333c"  Type                : NFS  Path                : \\LinuxSRV2049\Reports  AccessCredentials   :  ProcessingMode      : Direct  StorageSnapshotPath :  ProxyMode           : Automatic  SelectedProxyServer : {}  Id                  : 678eafe4-ad76-4878-8230-561b4226333c  CacheRepository     : Veeam.Backup.Core.CBackupRepository | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting File Share by Backup

|  |  |
| --- | --- |
| This example shows how to get the Fileserv05 (SMB) DB file shares by the backup that protects them. The cmdlet output will contain settings of these file shares.  |  | | --- | | $nasbackup = Get-VBRNASBackup -Name "Fileserv05 (SMB) DB"  Type                        : SMB |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasbackup variable. 2. Run the Get-VBRNASServer cmdlet. Set the $nasbackup variable as the Backup parameter value. |

Related Commands

[Get-VBRNASBackup](get-vbrnasbackup.md)


