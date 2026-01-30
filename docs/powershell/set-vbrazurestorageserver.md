---
title: "Set-VBRAzureStorageServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazurestorageserver.html"
last_updated: "7/15/2025"
product_version: "13.0.1.1071"
---

# Set-VBRAzureStorageServer


Short Description

Modifies settings of Microsoft Azure object storage added as unstructured data source to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAzureStorageServer -Server <VBRAzureStorageServer> [-Account <VBRAzureBlobAccount>] [-ProxyMode <VBRNASProxyMode>] [-SelectedProxyServer <VBRNASProxyServer[]>] [-CacheRepository <CBackupRepository>] [-BackupIOControlLevel <VBRUnstructuredBackupIOControlLevel>] [-MetaMigrationType <VBRUnstructuredBackupMetaMigrationType>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of  Microsoft Azure object storage added as unstructured data source to the inventory. You can modify settings of the following object storage repositories:

* Microsoft Azure Blob Storage
* Microsoft Azure Data Lake

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the Microsoft Azure object storage that you want to modify. | Accepts the VBRAzureBlobServer object. To create this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Account | Specifies Microsoft Azure credentials records.The cmdlet will use these credentials record to connect to object storage. | Accepts the VBRAzureBlobAccount object. To get this object, run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. | False | Named | True (ByValue) |
| ProxyMode | Specifies the backup proxy options.   * Automatic: use this option if you want Veeam Backup & Replication to choose the backup proxy that will process object storage. * SelectedProxy: use this option if you want to specify the backup proxy that will process object storage. | VBRNASProxyMode | False | Named | False |
| SelectedProxyServer | For the SelectedProxy option of the ProxyMode parameter.  Specifies the backup proxy. Veeam Backup & Replication will use this backup proxy to back up Microsoft Azure object storage. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the .VCACHE files on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from object storage. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRUnstructuredBackupIOControlLevel | False | Named | False |
| MetaMigrationType | Specifies how the cmdlet will migrate metadata. You can use one of the following options:   * CheckExistence — use this option to check that metadata is available on the current cache repository. * CopyMetaFromCache — use this option to migrate metadata from source cache repository to a new cache repository. * DownloadMetaFromArchive — use this option to migrate metadata from archive repository or from replica metadata in archive repository. | VBRUnstructuredBackupMetaMigrationType | False | Named | False |
|  |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureStorageServer](vbrazurestorageserver.md)

Examples

Modifying Settings of Microsoft Azure Data Lake Added as Unstructured Data Source

This example shows how to set the high speed for Veeam Backup & Replication to read data from Microsoft Azure Data Lake object storage added as unstructured data source to the inventory.

|  |
| --- |
| $server = Get-VBRUnstructuredServer -Name "Azure OS"  Set-VBRAzureStorageServer -Server $server -BackupIOControlLevel High |

Perform the following steps:

1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter values. Save the result to the $server variable.
2. Run the Set-VBRAzureStorageServer cmdlet. Set the $server variable as the Server parameter value. Set the High option for the BackupIOControlLevel parameter.

Related Commands

[Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)


