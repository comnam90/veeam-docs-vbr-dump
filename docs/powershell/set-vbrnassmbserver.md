---
title: "Set-VBRNASSMBServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnassmbserver.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBRNASSMBServer

In this article

Short Description

Modifies settings of SMB network shared folders added to the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify settings of SMB network shared folders without authentication.

|  |
| --- |
| Set-VBRNASSMBServer -Server <VBRNASSMBServer> [-RequireAccessCredentials] [-ProcessingMode <VBRNASProcessingMode>{Direct | VSSSnapshot | StorageSnapshot}] [-ProxyMode <VBRNASProxyMode> {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-CacheRepository <CBackupRepository>] [-MetaMigrationType <VBRNASBackupMetaMigrationType>] [-StorageSnapshotPath <string>] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-EnableDirectBackupFailover]  [<CommonParameters>] |

* Modify settings of SMB network shared folders with the user name and password.

|  |
| --- |
| Set-VBRNASSMBServer -Server <VBRNASSMBServer> -User <string> -Password <string> [-RequireAccessCredentials] [-ProcessingMode <VBRNASProcessingMode> {Direct | VSSSnapshot | StorageSnapshot}] [-ProxyMode <VBRNASProxyMode> {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-CacheRepository <CBackupRepository>] [-MetaMigrationType <VBRNASBackupMetaMigrationType>] [-StorageSnapshotPath <string>] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-EnableDirectBackupFailover]  [<CommonParameters>] |

* Modify settings of SMB network shared folders using credentials.

|  |
| --- |
| Set-VBRNASSMBServer -Server <VBRNASSMBServer> -AccessCredentials <CCredentials> [-RequireAccessCredentials] [-ProcessingMode <VBRNASProcessingMode> {Direct | VSSSnapshot | StorageSnapshot}] [-ProxyMode <VBRNASProxyMode> {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-CacheRepository <CBackupRepository>] [-MetaMigrationType <VBRNASBackupMetaMigrationType>] [-StorageSnapshotPath <string>] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-EnableDirectBackupFailover]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of SMB network shared folders added to the Veeam Backup & Replication infrastructure. This cmdlet modifies an existing VMware replication job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies an array of SMB network shared folders that you want to modify. | Accepts the VBRNASSMBServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| User | Specifies the user name. The cmdlet will apply this user name to authenticate against the SMB network shared folder.  Note: The user name must be in the DOMAIN\Username format. | String | True | Named | False |
| Password | Specifies the password. The cmdlet will use this password to authenticate against the SMB network shared folder. | String | True | Named | False |
| AccessCredentials | Specifies credentials that the cmdlet will use to authenticate against the SMB network shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| RequireAccessCredentials | Defines that the cmdlet will check whether Veeam Backup & Replication uses authentication to access the SMB network shared folder.  If you do not provide this parameter, the cmdlet will not check credentials that are used to access the SMB network shared folder.  To remove credentials, specify the RequireAccessCredentials parameter with the :$False value.  Note: If credentials are not provided, the cmdlet will return an error. To avoid the error, you must specify credentials using either of the following parameters:   * User and Password * AccessCredentials | SwitchParamter | False | Named | False |
| ProcessingMode | Specifies processing options that define how Veeam Backup & Replication will back up data.   * Direct: use this option to back up directly from the SMB network shared folder. * VSSSnapshot: use this option to back up from VSS snapshots that have been created by the backup proxy. * StorageSnapshot: use this option to back up from the native storage snapshots. | VBRNASProcessingMode | False | Named | False |
| ProxyMode | Specifies the backup proxy options.   * Automatic: use this option if you want Veeam Backup & Replication to choose the backup proxy that will process the SMB network shared folder. * SelectedProxy: use this option if you want to specify the backup proxy that will process the SMB network shared folder. Use the SelectedProxyServer parameter to specify the backup proxy. | VBRNASProxyMode | False | Named | False |
| SelectedProxyServer | For the SelectedProxy option of the ProxyMode parameter.  Specifies the backup proxy. Veeam Backup & Replication will use this backup proxy to back up the SMB network shared folder. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the cached data of the SMB network shared folder on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| MetaMigrationType | Specifies how the cmdlet will migrate metadata. You can use one of the following options:   * CheckExistence — use this option to check that metadata is available on the current cache repository. * CopyMetaFromCache — use this option to migrate metadata from source cache repository to a new cache repository. Note: If metadata in a source cache repository is corrupted, the cmdlet will copy data from the archive repository. * DownloadMetaFromArchive — use this option to migrate metadata from archive repository or from replica metadata in archive repository. | VBRNASBackupMetaMigrationType | False | Named | False |
| StorageSnapshotPath | For the StorageSnapshot processing options.  Specifies the path to the folder where native storage snapshots are located. Veeam Backup & Replication will get data from these snapshots located at the specified folder. | String | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from the file server. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRNASBackupIOControlLevel | False | Named | False |
| EnableDirectBackupFailover | For the StorageSnapshot processing option.  Defines that if the native storage snapshot fails while being processed, Veeam Backup & Replication will backup data directly from the file server. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASSMBServer object that contains settings of the SMB network shared folder that is added to the Veeam Backup & Replication infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Processing Options

|  |  |
| --- | --- |
| This example shows how to modify the processing options of the \\WinSRV2049\Documents SMB network shared folder. Veeam Backup & Replication will create backups of the \\WinSRV2049\Documents SMB network shared folder from the native storage snapshots that have been created by the backup proxy.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name '\\WinSRV2049\Documents'  Set-VBRNASSMBServer -Server $server -ProcessingMode StorageSnapshot |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Set-VBRNASSMBServer cmdlet. Set the $server variable as the Server parameter value. Set the StorageSnapshot value as the ProcessingMode parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying User Name and Password

|  |  |
| --- | --- |
| This example shows how to modify the user name and the password that are used to access the \\WinSRV2049\Reports SMB network shared folder.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name '\\WinSRV2049\Reports'  Set-VBRNASSMBServer -Server $server -RequireAccessCredentials -User Administrator -Password Pa$$word |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Set-VBRNASSMBServer cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Provide the RequireAccessCredentials parameter. * Specify the User parameter. * Specify the Password parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Credentials

|  |  |
| --- | --- |
| This example shows how to modify credentials that are used to access the \\WinSRV2049\January SMB network shared folder.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name '\\WinSRV2049\January'  $credentials = Get-VBRCredentials  Set-VBRNASSMBServer -Server $server -RequireAccessCredentials -Credentials $credentials |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $credentials variable. 3. Run the Set-VBRNASSMBServer cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Provide the RequireAccessCredentials parameter. * Set the $credentials variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Modifying Backup Proxy Options

|  |  |
| --- | --- |
| This example shows how to modify the backup proxy options of the \\WinSRV2049\October SMB network shared folder. The SMB network shared folder will be processed by the Proxy09 backup proxy.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name '\\WinSRV2049\October'  $proxy = Get-VBRNASProxyServer -Name 'Proxy09'  Set-VBRNASSMBServer -Server $server -ProxyMode SelectedProxy -SelectedProxyServer $proxy |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 3. Run the Set-VBRNASSMBServer cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Set the SelectedProxy option for the ProxyMode parameter. * Set the $proxy variable as the SelectedProxyServer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Modifying Cache Repository Settings

|  |  |
| --- | --- |
| This example shows how to modify cache repository settings of the \\WinSRV2049\Documents SMB network shared folder. The \\WinSRV2049\Documents SMB network shared folder will be processed by the Repository09 backup repository.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name '\\WinSRV2049\Documents'  $repository = Get-VBRBackupRepository -Name 'Repository09'  Set-VBRNASSMBServer -Server $server -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Set-VBRNASSMBServer cmdlet. Set the $server variable as the Server parameter value. Set the $repository variable as the CacheRepository parameter value. |

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [Get-VBRNASProxyServer](get-vbrnasproxyserver.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
