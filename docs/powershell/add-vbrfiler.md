---
title: "Add-VBRFiler"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrfiler.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# Add-VBRFiler

In this article

Short Description

Adds an enterprise NAS system as a file share to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add an enterprise NAS system as a file share to the inventory without authentication.

|  |
| --- |
| Add-VBRFiler -StorageServer <IHost> -CacheRepository <CBackupRepository> [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-EnableSnapDiff]  [<CommonParameters>] |

* Add an enterprise NAS system as a file share to the inventory with user name and password.

|  |
| --- |
| Add-VBRFiler -StorageServer <IHost> -User <string> -Password <string> -CacheRepository <CBackupRepository> [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-EnableSnapDiff]  [<CommonParameters>] |

* Add an enterprise NAS system as a file share to the inventory using credentials.

|  |
| --- |
| Add-VBRFiler -StorageServer <IHost> -AccessCredentials <CCredentials> -CacheRepository <CBackupRepository> [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-EnableSnapDiff]  [<CommonParameters>] |

Detailed Description

This cmdlet adds an enterprise NAS system as a file share to the inventory.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| StorageServer | Specifies the storage server where the file share is located. The cmdlet will add this storage server as a file share to the inventory. | Accepts the IHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the .VCACHE files on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from the file server. You can specify one of the following speed:   * Lowest * Low * Medium * High * Highest | VBRNASBackupIOControlLevel | False | Named | False |
| EnableSnapDiff | Use this parameter for Dell PowerScale (formerly Isilon) storages only.  Defines that during the file backup jobs Veeam Backup & Replication will use the file change tracking technology provided by the NAS manufacturer. | SwitchParameter | False | Named | False |
| User | Specifies the user name. The cmdlet will apply this user name to authenticate against the enterprise NAS system. | String | True | Named | False |
| Password | Specifies the password. The cmdlet will use this password to authenticate against the enterprise NAS system. | String | True | Named | False |
| AccessCredentials | Specifies credentials that the cmdlet will use to authenticate against the enterprise NAS system. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRFiler object that defines the settings of the enterprise NAS system added as a file share to the inventory.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Enterprise NAS System as File Share Without Authentication

|  |  |
| --- | --- |
| This example shows how to add the ontap-2 enterprise NAS system as a file share to the inventory without authentication. The cmdlet will set the Backup Repository 05 as the cache repository.  |  | | --- | | $netapp = Get-NetAppHost -Name 'ontap-2'  $repository = Get-VBRBackupRepository -Name "Backup Repository 05"  Add-VBRFiler -StorageServer $netapp -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $netapp variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Add-VBRFiler cmdlet. Specify the following settings:  * Set the $netapp variable as the StorageServer parameter value. * Set the $repository variable as the CacheRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Enterprise NAS System as File Share with User Name and Password

|  |  |
| --- | --- |
| This example shows how to add the ontap-2 enterprise NAS system as a file share to the inventory with user name and password. The cmdlet will set the Backup Repository 05 as the cache repository.  |  | | --- | | $netapp = Get-NetAppHost -Name 'ontap-2'  $repository = Get-VBRBackupRepository -Name 'Backup Repository 05'  Add-VBRFiler -StorageServer $netapp -User Administrator -Password AdminCredentials -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $netapp variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Add-VBRFiler cmdlet. Specify the following settings:  * Set the $netapp variable as the StorageServer parameter value.  * Specify the User parameter value. * Specify the Password parameter value.  * Set the $repository variable as the CacheRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding Enterprise NAS System as a File Share with Credentials

|  |  |
| --- | --- |
| This example shows how to add the ontap-2 enterprise NAS system as a file share to the inventory with credentials. The cmdlet will set the Backup Repository 05 as the cache repository.  |  | | --- | | $netapp = Get-NetAppHost -Name 'ontap-2'  $repository = Get-VBRBackupRepository -Name 'Backup Repository 05'  $credentials = Get-VBRCredentials -Name "Veeam Administrator"  Add-VBRFiler -StorageServer $netapp -AccessCredentials $credentials -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $netapp variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable. 4. Run the Add-VBRFiler cmdlet. Specify the following settings:  * Set the $netapp variable as the StorageServer parameter value.  * Set the $credentials variable as the AccessCredentials parameter value.  * Set the $repository variable as the CacheRepository parameter value. |

Related Commands

* [Get-NetAppHost](get-netapphost.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 9/4/2024

Page content applies to build 13.0.1.1071
