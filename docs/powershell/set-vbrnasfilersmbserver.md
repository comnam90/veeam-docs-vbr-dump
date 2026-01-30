---
title: "Set-VBRNasFilerSMBServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasfilersmbserver.html"
last_updated: "4/29/2024"
product_version: "13.0.1.1071"
---

# Set-VBRNasFilerSMBServer


Short Description

Modifies settings of SMB shares located on an enterprise NAS system added to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify settings of SMB shares located on an enterprise NAS system added to the inventory. The cmdlet will modify settings without authentication.

|  |
| --- |
| Set-VBRNasFilerSMBServer -Server <VBRSANNASSMBServer> [-CacheRepository <CBackupRepository>] [-MetaMigrationType {CheckExistence | CopyMetaFromCache | DownloadMetaFromArchive}] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}]  [<CommonParameters>] |

* Modify settings of SMB shares located on an enterprise NAS system added to the inventory. The cmdlet will modify settings using specific user name and password.

|  |
| --- |
| Set-VBRNasFilerSMBServer -Server <VBRSANNASSMBServer> [-User <string>] [-Password <string>] [-CacheRepository <CBackupRepository>] [-MetaMigrationType {CheckExistence | CopyMetaFromCache | DownloadMetaFromArchive}] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}]  [<CommonParameters>] |

* Modify settings of SMB shares located on an enterprise NAS system added to the inventory. The cmdlet will modify settings using specific credentials.

|  |
| --- |
| Set-VBRNasFilerSMBServer -Server <VBRSANNASSMBServer> [-AccessCredentials <CCredentials>] [-CacheRepository <CBackupRepository>] [-MetaMigrationType {CheckExistence | CopyMetaFromCache | DownloadMetaFromArchive}] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}]  [<CommonParameters>] |

* Modify settings of SMB shares located on an enterprise NAS system added to the inventory. The SMB file share will inherit settings of the enterprise NAS system.

|  |
| --- |
| Set-VBRNasFilerSMBServer -Server <VBRSANNASSMBServer> -InheritSettingsFromFiler [-MetaMigrationType {CheckExistence | CopyMetaFromCache | DownloadMetaFromArchive}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of SMB shares located on an enterprise NAS system and added to the inventory. You can either specify the cache repository manually or make the file share to inherit cache repository settings from the enterprise NAS system.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies an SMB file share. The cmdlet will modify settings for this file share. | Accepts the VBRSANNASSMBServer (VBRNASServer) object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| InheritSettingsFromFiler | Defines that the SMB file share will inherit settings of the enterprise SMB system. If you provide this parameter, the cmdlet will inherit cache settings, throttling settings and credentials.  Note: You must provide the MetaMigrationType to inherit cache repository settings. | SwitchParameter | True | Named | False |
| CacheRepository | Specifies a cache repository. The cmdlet will set this repository as a cache repository for the SMB file share. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| User | Specifies the user name. The cmdlet will apply this user name to authenticate against the enterprise NAS system. | String | False | Named | False |
| Password | Specifies the password. The cmdlet will use this password to authenticate against the enterprise NAS system. | String | False | Named | False |
| AccessCredentials | Specifies credentials that the cmdlet will use to authenticate against the enterprise NAS system. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| MetaMigrationType | Specifies how the cmdlet will migrate metadata. You can use one of the following options:   * CheckExistence — use this option to check that metadata is available on the current cache repository. * CopyMetaFromCache — use this option to migrate metadata from source cache repository to a new cache repository.   Note: If metadata in a source cache repository is corrupted, the cmdlet will copy data from the archive repository.   * DownloadMetaFromArchive — use this option to migrate metadata from archive repository or from replica metadata in archive repository. | VBRNASBackupMetaMigrationType | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from the file server. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRNASBackupIOControlLevel | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASServer object that defines settings of the SMB file share located on the enterprise NAS system.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting Cache Repository for SMB Share Manually

|  |  |
| --- | --- |
| This example shows how to modify SMB share: a cache repository is specified manually.  |  | | --- | | $isilonhost = Get-VBRIsilonHost -Name "HostName"  $volume = Get-VBRIsilonVolume -Name "SMB Share" -Host $isilonhost  $isi = Get-VBRUnstructuredServer -SANEntity $volume  $cacherepo = Get-VBRBackupRepository -Name "Cache repository 1"  Set-VBRNasFilerSMBServer -Server $isi -CacheRepository $cacherepo |  Perform the following steps:   1. Run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. Specify the Name parameter value. Save the result to the $isilonhost variable. 2. Run the [Get-VBRIsilonVolume](get-vbrisilonvolume.md) cmdlet. Specify the Name parameter value. Set the $isilonhost variable as the Host parameter value. Save the result to the $volume variable. 3. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Set the $volume variable as the SANEntity parameter value. Save the result to the $volume variable. 4. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $cacherepo variable. 5. Run the Set-VBRNasFilerSMBServer cmdlet. Set the $isi variable as the Server parameter value. Set the $cacherepo variable as the CacheRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Cache Repository Settings Inherited from NAS System for SMB Share

|  |  |
| --- | --- |
| This example shows how to modify SMB share: a cache repository settings are inherited from the enterprise NAS system on which the share is located.  |  | | --- | | $isilonhost = Get-VBRIsilonHost -Name "HostName"  $volume = Get-VBRIsilonVolume -Name "SMB Share" -Host $isilonhost  $isi = Get-VBRUnstructuredServer -SANEntity $volume  Set-VBRNasFilerSMBServer -Server $isi -InheritSettingsFromFiler |  Perform the following steps:   1. Run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. Specify the Name parameter value. Save the result to the $isilonhost variable. 2. Run the [Get-VBRIsilonVolume](get-vbrisilonvolume.md) cmdlet. Specify the Name parameter value. Set the $isilonhost variable as the Host parameter value. Save the result to the $volume variable. 3. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Set the $volume variable as the SANEntity parameter value. Save the result to the $volume variable. 4. Run the Set-VBRNasFilerSMBServer cmdlet. Set the $isi variable as the Server parameter value. Provide the InheritSettingsFromFiler parameter. |

Related Commands

* [Get-VBRIsilonHost](get-vbrisilonhost.md)
* [Get-VBRIsilonVolume](get-vbrisilonvolume.md)
* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


