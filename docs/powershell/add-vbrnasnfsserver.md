---
title: "Add-VBRNASNFSServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrnasnfsserver.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Add-VBRNASNFSServer

In this article

Short Description

Adds NFS network shared folders to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRNASNFSServer -Path <string> -CacheRepository <CBackupRepository> [-ProcessingMode {Direct | VSSSnapshot | StorageSnapshot}] [-ProxyMode {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-StorageSnapshotPath <string>] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-EnableDirectBackupFailover] [-Encoding {utf | ansi}]  [<CommonParameters>] |

Detailed Description

This cmdlet adds NFS network shared folders to the inventory.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies a path to the NFS network shared folder. The cmdlet will add the NFS network shared folder located at the specified path to the inventory.  Note: Use the server:/folder format. | String | True | Named | False |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the .VCACHE files on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| ProcessingMode | Specifies processing options that define how Veeam Backup & Replication will back up data.   * Direct: use this option to back up directly from the NFS network shared folder. * StorageSnapshot: use this option to back up from the native storage snapshots.   Note: The VSSSnapshot option does not work with the NFS network shared folders. | VBRNASProcessingMode | False | Named | False |
| StorageSnapshotPath | For the StorageSnapshot processing options.  Specifies the path to the folder where native storage snapshots are located. Veeam Backup & Replication will get data from these snapshots located at the specified folder. | String | False | Named | False |
| ProxyMode | Specifies the backup proxy options.   * Automatic: use this option if you want Veeam Backup & Replication to choose the backup proxy that will process the NFS network shared folder. * SelectedProxy: use this option if you want to specify the backup proxy that will process the NFS network shared folder. Use the SelectedProxyServer parameter to specify the backup proxy. | VBRNASProxyMode | False | Named | False |
| SelectedProxyServer | For the SelectedProxy option of the ProxyMode parameter.  Specifies the backup proxy. Veeam Backup & Replication will use this backup proxy to process the NFS network shared folder. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from the file server. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRNASBackupIOControlLevel | False | Named | False |
| EnableDirectBackupFailover | For the StorageSnapshot processing option.  Defines that if the native storage snapshot fails while being processed, Veeam Backup & Replication will back up data directly from the file server. | SwitchParameter | False | Named | False |
| Encoding | Specifies encoding for NFS share. You can specify either of the following values:   * utf * ansi | VBRNASEncoding | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASNFSServer object that contains settings of the NFS network shared folder that is added to the Veeam Backup & Replication infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding NFS Network Shared Folder

|  |  |
| --- | --- |
| This example shows how to add the NFS shared folder to the inventory.  |  | | --- | | $repository = Get-VBRBackupRepository -Name 'Backup Repository 08'  Add-VBRNASNFSServer -Path 'Server06:/SharedDocuments' -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Add-VBRNASNFSServer cmdlet. Specify the Path parameter value. Set the $repository variable as the CacheRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding NFS Network Shared Folder with Direct Processing

|  |  |
| --- | --- |
| This example shows how to add the NFS shared folder to the inventory. Veeam Backup & Replication will back up data directly from the NFS network shared folder.  |  | | --- | | $repository = Get-VBRBackupRepository -Name 'Backup Repository 02'  Add-VBRNASNFSServer -Path 'Server06:/SharedDocuments' -CacheRepository $repository -ProcessingMode Direct |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Add-VBRNASNFSServer cmdlet. Specify the following settings:  * Specify the Path parameter value. * Set the $repository variable as the CacheRepository parameter value. * Set the Direct option for the ProcessingMode parameter. |

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
