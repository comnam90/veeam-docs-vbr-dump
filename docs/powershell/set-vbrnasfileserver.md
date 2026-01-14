---
title: "Set-VBRNASFileServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasfileserver.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Set-VBRNASFileServer

In this article

Short Description

Modifies managed Windows or Linux file serves added to the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNASFileServer -Server <VBRNASFileServer> [-CacheRepository <CBackupRepository>]  [-MetaMigrationType <VBRNASBackupMetaMigrationType>] [-BackupIOControlLevel <VBRNASBackupIOControlLevel>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies managed Windows or Linux file serves added to the Veeam Backup & Replication infrastructure. This cmdlet modifies an existing VMware replication job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specify a file server. The cmdlet will modify settings of this file server. | Accepts the VBRNASNFSServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| CacheRepository | Specifies the cache repository that you want to modify. Veeam Backup & Replication will keep the cached data of the file server on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| MetaMigrationType | Specifies how the cmdlet will migrate metadata. You can use one of the following options:   * CheckExistence — use this option to check that metadata is available on the current cache repository. * CopyMetaFromCache — use this option to migrate metadata from source cache repository to a new cache repository. * DownloadMetaFromArchive — use this option to migrate metadata from archive repository or from replica metadata in archive repository. | VBRNASBackupMetaMigrationType | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from the file server. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRNASBackupIOControlLevel | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASFileServer object that contains settings of the managed Windows or Linux file serves added to the Veeam Backup & Replication infrastructure.

Examples

Modifying Cache Repository

This example shows how to modify a cache repository of the file server. The cmdlet will set the Repository 04 repository as the cache repository on this server.

|  |
| --- |
| $server = Get-VBRUnstructuredServer -Name 'File server 09'  $cacherepository = Get-VBRBackupRepository -Name 'Repository 04'  Set-VBRNASFileServer -Server $server -CacheRepository $cacherepository |

Perform the following steps:

1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $cacherepository variable.
3. Run the Set-VBRNASFileServer cmdlet. Set the $server variable as the Server parameter value. Specify the $cacherepository variable as the CacheRepository parameter value.

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 3/4/2024

Page content applies to build 13.0.1.1071
