---
title: "Add-VBRAzureStorageServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrazurestorageserver.html"
last_updated: "7/15/2025"
product_version: "13.0.1.1071"
---

# Add-VBRAzureStorageServer

In this article

Short Description

Adds Microsoft Azure object storage as unstructured data source to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAzureStorageServer -FriendlyName <String> -Account <VBRAzureBlobAccount> -RegionType <VBRAzureBlobRegionType> [-ProxyMode <VBRNASProxyMode>] [-SelectedProxyServer <VBRNASProxyServer[]>] -CacheRepository <CBackupRepository> [-BackupIOControlLevel <VBRUnstructuredBackupIOControlLevel>] [-UseChangeFeed] [<CommonParameters>] |

Detailed Description

This cmdlet adds Microsoft Azure object storage as unstructured data source to the inventory. You can add the following object storage repositories:

* Microsoft Azure Blob Storage
* Microsoft Azure Data Lake

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FriendlyName | Specify a name that you want to assign to the object storage. | String | True | Named | True (ByValue) |
| Account | Specifies Microsoft Azure credentials records. The cmdlet will use these credentials record to connect to object storage. | Accepts the VBRAzureBlobAccount object. To get this object, run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. | True | Named | False |
| RegionType | Specifies the region type of Microsoft Azure storage. The cmdlet will connect to the selected region type and will set up a connection with Microsoft Azure storage. You can select the following types of regions:   * Global * Government * China | VBRAzureBlobRegionType | True | Named | False |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the .VCACHE files on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| ProxyMode | Specifies the backup proxy options.   * Automatic: use this option if you want Veeam Backup & Replication to choose the backup proxy that will process object storage. * SelectedProxy: use this option if you want to specify the backup proxy that will process object storage. | VBRNASProxyMode | False | Named | False |
| SelectedProxyServer | For the SelectedProxy option of the ProxyMode parameter.  Specifies the backup proxy. Veeam Backup & Replication will use this backup proxy to back up Microsoft Azure object storage. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from object storage. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRUnstructuredBackupIOControlLevel | False | Named | False |
|  |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureStorageServer](vbrazurestorageserver.md)

Examples

Adding Microsoft Azure Data Lake as Unstructured Data Source

This example shows how to add Microsoft Azure Data Lake object storage as unstructured data source to the inventory.

|  |
| --- |
| $creds = Add-VBRAzureBlobAccount -Name "string" -SharedKey "string”  $cacherepository = Get-VBRBackupRepository -Name "WinSrv"  Add-VBRAzureStorageServer -FriendlyName "Azure Blob" -Account $creds -RegionType Global -CacheRepository $cacherepository |

Perform the following steps:

1. Run the [Add-VBRAzureBlobAccount](add-vbrazureblobaccount.md) cmdlet. Specify the Name and the SharedKey parameters values. Save the result to the $creds variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $cacherepository variable.
3. Run the Add-VBRAzureStorageServer cmdlet. Specify the following settings:

* Specify the FriendlyName parameter value.
* Set the $creds variable as the Account parameter value.
* Set the Global option for the RegionType parameter.
* Set the $cacherepository variable as the CacheRepository parameter value.

Related Commands

* [Add-VBRAzureBlobAccount](add-vbrazureblobaccount.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRNASProxyServer](get-vbrnasproxyserver.md)

Page updated 7/15/2025

Page content applies to build 13.0.1.1071
