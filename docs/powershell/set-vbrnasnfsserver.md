---
title: "Set-VBRNASNFSServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasnfsserver.html"
last_updated: "4/29/2024"
product_version: "13.0.1.1071"
---

# Set-VBRNASNFSServer


Short Description

Modifies settings of NFS shared folders added to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNASNFSServer -Server <VBRNASNFSServer> [-ProcessingMode <VBRNASProcessingMode> {Direct | VSSSnapshot |StorageSnapshot}] [-ProxyMode <VBRNASProxyMode> {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-CacheRepository <CBackupRepository>] [-MetaMigrationType <VBRNASBackupMetaMigrationType>] [-StorageSnapshotPath <string> [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-EnableDirectBackupFailover] [-Encoding {utf | ansi}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of NFS network shared folders added to the inventory. This cmdlet modifies an existing VMware replication job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specify an NFS network shared folder. The cmdlet will modify settings of this network shared folder. | Accepts the VBRNASNFSServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ProcessingMode | Specifies processing options that define how Veeam Backup & Replication will back up data.   * Direct: use this option to back up directly from the SMB network shared folder. * VSSSnapshot: use this option to back up from VSS snapshots that have been created by the backup proxy. * StorageSnapshot: use this option to back up from the native storage snapshots that have been created by the backup proxy. | VBRNASProcessingMode | False | Named | False |
| StorageSnapshotPath | For the StorageSnapshot processing options.  Specifies the path to the folder where native storage snapshots are located. Veeam Backup & Replication will get data from these snapshots located at the specified folder. | String | False | Named | False |
| ProxyMode | Specifies the backup proxy options.   * Automatic: use this option if you want Veeam Backup & Replication to choose the backup proxy that will process the NFS network shared folder. * SelectedProxy: use this option if you want to specify the backup proxy that will process the NFS network shared folder. | VBRNASProxyMode | False | Named | False |
| SelectedProxyServer | For the SelectedProxy option of the ProxyMode parameter.  Specifies the backup proxy. Veeam Backup & Replication will use this backup proxy to process the NFS network shared folder. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the cached data of the NFS network shared folder on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| MetaMigrationType | Specifies how the cmdlet will migrate metadata. You can use one of the following options:   * CheckExistence — use this option to check that metadata is available on the current cache repository. * CopyMetaFromCache — use this option to migrate metadata from source cache repository to a new cache repository. Note: If metadata in a source cache repository is corrupted, the cmdlet will copy data from the archive repository. * DownloadMetaFromArchive — use this option to migrate metadata from archive repository or from replica metadata in archive repository. | VBRNASBackupMetaMigrationType | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from the file server. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRNASBackupIOControlLevel | False | Named | False |
| EnableDirectBackupFailover | Enables the StorageSnapshot processing option.  Defines that if the native storage snapshot fails while being processed, Veeam Backup & Replication will backup data directly from the file server. | SwitchParameter | False | Named | False |
| Encoding | Specifies encoding for NFS share. You can specify either of the following values:   * utf * ansi | VBRNASEncoding | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASNFSServer object that contains settings of the NFS network shared folder that is added to the inventory.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Processing Options

|  |  |
| --- | --- |
| This example shows how to modify the processing options of the \\LinuxSRV2049\November NFS network shared folder. Veeam Backup & Replication will create backups of the \\LinuxSRV2049\November NFS network shared folder from VSS snapshots that have been created by the backup proxy.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name '\\LinuxSRV2049\November'  Set-VBRNASNFSServer -Server $server -ProcessingMode VSSSnapshot |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Set-VBRNASNFSServer cmdlet. Set the $server variable as the Server parameter value. Set the VSSSnapshot option for the ProcessingMode parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Backup Proxy Options

|  |  |
| --- | --- |
| This example shows how to modify the backup proxy options of the \\LinuxSRV2049\November NFS network shared folder. Veeam Backup & Replication will select the backup proxy to process the \\LinuxSRV2049\November NFS network shared folder automatically.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name '\\LinuxSRV2049\November'  Set-VBRNASNFSServer -Server $server -ProxyMode Automatic |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Set-VBRNASSMBServer cmdlet. Set the $server variable as the Server parameter value. Set the Automatic value as the ProxyMode parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Cache Repository Settings

|  |  |
| --- | --- |
| This example shows how to modify cache repository settings of the \\LinuxSRV2049\November NFS network shared folder. The \\LinuxSRV2049\November NFS network shared folder will be processed by the Repository07 backup repository.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name '\\LinuxSRV2049\November'  $repository = Get-VBRBackupRepository -Name 'Repository07'  Set-VBRNASSMBServer -Server $server -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Set-VBRNASSMBServer cmdlet. Set the $server variable as the Server parameter value. Set the $repository variable as the CacheRepository parameter value. |

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


