---
title: "Add-VBRNASSMBServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrnassmbserver.html"
last_updated: "6/17/2025"
product_version: "13.0.1.1071"
---

# Add-VBRNASSMBServer

In this article

Short Description

Adds SMB network shared folders to the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add SMB network shared folders to the Veeam Backup & Replication infrastructure without authentication.

|  |
| --- |
| Add-VBRNASSMBServer -Path <string> -CacheRepository <CBackupRepository> [-ProcessingMode <VBRNASProcessingMode> {Direct | VSSSnapshot | StorageSnapshot}] [-ProxyMode <VBRNASProxyMode> {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-StorageSnapshotPath <string>] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}][-EnableDirectBackupFailover]  [<CommonParameters>] |

* Add SMB network shared folders to the Veeam Backup & Replication infrastructure with user name and password.

|  |
| --- |
| Add-VBRNASSMBServer -Path <string> -User <string> -Password <string> -CacheRepository <CBackupRepository> [-ProcessingMode <VBRNASProcessingMode> {Direct | VSSSnapshot | StorageSnapshot}] [-ProxyMode <VBRNASProxyMode> {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-StorageSnapshotPath <string>] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-EnableDirectBackupFailover]  [<CommonParameters>] |

* Add SMB network shared folders to the Veeam Backup & Replication infrastructure using credentials.

|  |
| --- |
| Add-VBRNASSMBServer -Path <string> -AccessCredentials <CCredentials> -CacheRepository <CBackupRepository> [-ProcessingMode <VBRNASProcessingMode> {Direct | VSSSnapshot | StorageSnapshot}] [-ProxyMode <VBRNASProxyMode> {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-StorageSnapshotPath <string>] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-EnableDirectBackupFailover]  [<CommonParameters>] |

Detailed Description

This cmdlet adds SMB network shared folders to the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies a path to the SMB network shared folder. The cmdlet will add the SMB network shared folder located at the specified path to the Veeam Backup & Replication infrastructure.  Note: Use the \\server\folder format. | String | True | Named | False |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the .VCACHE files on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| User | Specifies the user name. The cmdlet will apply this user name to authenticate against the SMB network shared folder.  Note: The user name must be in the DOMAIN\Username format. | String | True | Named | False |
| Password | Specifies the password. The cmdlet will use this password to authenticate against the SMB network shared folder. | String | True | Named | False |
| AccessCredentials | Specifies credentials that the cmdlet will use to authenticate against the SMB network shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| ProcessingMode | Specifies processing options that define how Veeam Backup & Replication will back up data.   * Direct: use this option to back up directly from the SMB network shared folder. * VSSSnapshot: use this option to back up from VSS snapshots that have been created by the backup proxy. * StorageSnapshot: use this option to back up from the native storage snapshots. | VBRNASProcessingMode | False | Named | False |
| StorageSnapshotPath | For the StorageSnapshot processing option.  Specifies the path to the folder where native storage snapshots are located. Veeam Backup & Replication will get data from these snapshots located at the specified folder. | String | False | Named | False |
| ProxyMode | Specifies the backup proxy options.   * Automatic: use this option if you want Veeam Backup & Replication to choose the backup proxy that will process the SMB network shared folder. * SelectedProxy: use this option if you want to specify the backup proxy that will process the SMB network shared folder. Use the SelectedProxyServer parameter to specify the backup proxy. | VBRNASProxyMode | False | Named | False |
| SelectedProxyServer | For the SelectedProxy option of the ProxyMode parameter.  Specifies the backup proxy. Veeam Backup & Replication will use this backup proxy to back up the SMB network shared folder. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from the file server. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRNASBackupIOControlLevel | False | Named | False |
| EnableDirectBackupFailover | For the StorageSnapshot processing option.  Defines that if the native storage snapshot fails while being processed, Veeam Backup & Replication will backup data directly from the file server. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASSMBServer object that contains settings of the SMB network shared folder that is added to the Veeam Backup & Replication infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding SMB Network Shared Folder Without Authentication

|  |  |
| --- | --- |
| This example shows how to add the SMB network shared folder without authentication.  |  | | --- | | $repository = Get-VBRBackupRepository -Name 'Backup Repository 09'  Add-VBRNASSMBServer -Path '\\Server07\SharedDocuments' -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Add-VBRNASSMBServer cmdlet. Specify the Path parameter value. Set the $repository variable as the CacheRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding SMB Network Shared Folder with User Name and Password

|  |  |
| --- | --- |
| This example shows how to add the SMB network shared folder authenticated with user name and password.  |  | | --- | | $repository = Get-VBRBackupRepository -Name 'Backup Repository 05'  Add-VBRNASSMBServer -Path '\\Server08\SharedDocuments' -User Administrator -Password AdminCredentials -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Add-VBRNASSMBServer cmdlet. Specify the following settings:  * Specify the Path parameter value. * Specify the User parameter value. * Specify the Password parameter value. * Set the $repository variable as the CacheRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding SMB Network Shared Folder with Credentials

|  |  |
| --- | --- |
| This example shows how to add SMB network shared folder authenticated with credentials.  |  | | --- | | $repository = Get-VBRBackupRepository -Name 'Backup Repository 05'  $credentials = Get-VBRCredentials -Name 'SMB File Share Credentials'  Add-VBRNASSMBServer -Path '\\Server04\SharedDocuments' -AccessCredentials $credentials -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable. 3. Run the Add-VBRNASSMBServer cmdlet. Specify the following settings:  * Specify the Path parameter value. * Set the $credentials variable as the AccessCredentials parameter value. * Set the $repository variable as the CacheRepository parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 6/17/2025

Page content applies to build 13.0.1.1071
