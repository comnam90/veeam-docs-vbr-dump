---
title: "Add-VBRAmazonS3Server"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbramazons3server.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-VBRAmazonS3Server


Short Description

Adds Amazon S3 storage as unstructured data source to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAmazonS3Server -FriendlyName <string> -Account <VBRAmazonAccount> -Region <VBRAmazonS3Region> -CacheRepository <CBackupRepository> [-ProxyMode {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-BackupIOControlLevel <VBRUnstructuredBackupIOControlLevel> {Lowest | Low | Medium | High | Highest}] [-BucketName <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds Amazon S3 storage to the inventory. You can use this object storage as a source of data for object storage backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FriendlyName | Specifies a name that you want to assign to the object storage. | String | True | Named | True (ByValue) |
| Account | Specifies an Amazon S3 credentials record. Veeam Backup & Replication will use this credentials record to connect to Amazon S3 storage. | Accepts the [VBRAmazonAccount](vbramazonaccount.md) object. To get this object, run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. | True | Named | False |
| Region | Specifies an array of Amazon S3 regions where Amazon S3 buckets are located. The cmdlet will return an array of Amazon S3 buckets from these Amazon S3 regions. | Accepts the [VBRAmazonS3Region](vbramazons3region.md) object. To get this object, run the [Get-VBRAmazonS3Region](get-vbramazons3region.md) cmdlet. | True | Named | False |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the .VCACHE files on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| ProxyMode | Specifies the backup proxy options.   * Automatic: use this option if you want Veeam Backup & Replication to choose the backup proxy that will process object storage. * SelectedProxy: use this option if you want to specify the backup proxy that will process object storage. | VBRNASProxyMode | False | Named | False |
| SelectedProxyServer | For the SelectedProxy option of the ProxyMode parameter.  Specifies the backup proxy. Veeam Backup & Replication will use this backup proxy to back up Amazon S3 object storage. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from object storage. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRUnstructuredBackupIOControlLevel | False | Named | False |
| BucketName | Specifies a name of the Amazon S3 bucket. The cmdlet will connect to this bucket. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAmazonS3Server object that contains settings of Amazon S3 storage added to the inventory.

Examples

Adding Amazon S3 Storage as Unstructured Data Source

This example shows how to add Amazon S3 storage as unstructured data source to the inventory.

|  |
| --- |
| $account = Get-VBRAmazonAccount -AccessKey "XXXXXXXX" -Description "AWS account"  $region = Get-VBRAmazonS3Region -RegionId "eu-central-1"  $cacherepository = Get-VBRBackupRepository -Name "WinSrv"  Add-VBRAmazonS3Server -FriendlyName "Amazon S3 OS" -Account $account -Region $region -CacheRepository $cacherepository |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the AccessKey and the Description parameter values. Save the result to the $account variable.
2. Run the [Get-VBRAmazonS3Region](get-vbramazons3region.md) cmdlet. Specify the RegionId parameter value. Save the result to the $region variable.
3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $cacherepository variable.
4. Run the Add-VBRAmazonS3Server cmdlet. Specify the following settings:

* Specify the FriendlyName parameter value.
* Set the $account variable as the Account parameter value.
* Set the $region variable as the Region parameter value.
* Set the $cacherepository variable as the CacheRepository parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRAmazonS3Region](get-vbramazons3region.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


