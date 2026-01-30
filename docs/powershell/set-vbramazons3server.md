---
title: "Set-VBRAmazonS3Server"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbramazons3server.html"
last_updated: "9/2/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAmazonS3Server


Short Description

Modifies settings of Amazon S3 storage added as unstructured data source to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAmazonS3Server -Server <VBRAmazonS3Server> [-Account <VBRAmazonAccount>] [-ProxyMode {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-CacheRepository <CBackupRepository>] [-BackupIOControlLevel <VBRUnstructuredBackupIOControlLevel> {Lowest | Low | Medium | High | Highest}] [-MetaMigrationType VBRUnstructuredBackupMetaMigrationType {CheckExistence | CopyMetaFromCache | DownloadMetaFromArchive}] [-BucketName <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet mofidies settings of Amazon S3 storage added as unstructured data source to the inventory.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the Amazon S3 storage that you want to modify. | Accepts the VBRAmazonS3Server object. To create this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Account | Specifies an Amazon S3 credentials record. Veeam Backup & Replication will use this credentials record to connect to Amazon S3 storage. | Accepts the [VBRAmazonAccount](vbramazonaccount.md) object. To get this object, run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. | False | Named | True (ByValue) |
| ProxyMode | Specifies the backup proxy options.   * Automatic: use this option if you want Veeam Backup & Replication to choose the backup proxy that will process object storage. * SelectedProxy: use this option if you want to specify the backup proxy that will process object storage. | VBRNASProxyMode | False | Named | False |
| SelectedProxyServer | For the SelectedProxy option of the ProxyMode parameter.  Specifies the backup proxy. Veeam Backup & Replication will use this backup proxy to back up Amazon S3 object storage. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the .VCACHE files on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from object storage. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRUnstructuredBackupIOControlLevel | False | Named | False |
| MetaMigrationType | Specifies how the cmdlet will migrate metadata. You can use one of the following options:   * CheckExistence — use this option to check that metadata is available on the current cache repository. * CopyMetaFromCache — use this option to migrate metadata from source cache repository to a new cache repository. * DownloadMetaFromArchive — use this option to migrate metadata from archive repository or from replica metadata in archive repository. | VBRUnstructuredBackupMetaMigrationType | False | Named | False |
| BucketName | Specifies a name of the Amazon S3 bucket. The cmdlet will connect to this bucket. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAmazonS3Server object that contains settings of Amazon S3 storage added to the inventory.

Examples

Modifying Settings of Amazon S3 Storage Added as Unstructured Data Source

This example shows how to set the high speed for Veeam Backup & Replication to read data from Amazon S3 storage added as unstructured data source to the inventory.

|  |
| --- |
| $server = Get-VBRUnstructuredServer -Name "Amazon S3 OS"  Set-VBRAmazonS3Server -Server $server -BackupIOControlLevel High |

Perform the following steps:

1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the Set-VBRAmazonS3Server cmdlet. Set the $server variable as the Server parameter value. Set the High option for the BackupIOControlLevel parameter.

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [Get-VBRNASProxyServer](get-vbrnasproxyserver.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRAmazonAccount](get-vbramazonaccount.md)


