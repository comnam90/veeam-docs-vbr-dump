---
title: "Add-VBRS3CompatibleServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrs3compatibleserver.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-VBRS3CompatibleServer


Short Description

Adds S3 compatible object storage as unstructured data source to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRS3CompatibleServer -Account <VBRAmazonAccount> -FriendlyName <string> -ServicePoint <string> -CacheRepository <CBackupRepository> [-RegionId <string>] [-ProxyMode {Automatic | SelectedProxy}] [-SelectedProxyServer <VBRNASProxyServer[]>] [-BackupIOControlLevel <VBRUnstructuredBackupIOControlLevel> {Lowest | Low | Medium | High | Highest}] [-BucketName <string>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds S3 compatible object storage as unstructured data source to the inventory.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies an S3 credentials record. Veeam Backup & Replication will use this credentials record to connect to S3 compatible object storage. | Accepts the [VBRAmazonAccount](vbramazonaccount.md) object. To get this object, run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. | True | Named | True (ByValue) |
| FriendlyName | Specify a name that you want to assign to the object storage. | String | True | Named | False |
| ServicePoint | Specifies a service point address of object storage. | String | True | Named | False |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the .VCACHE files on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| RegionId | Specifies a region. | String | False | Named | False |
| ProxyMode | Specifies the backup proxy options.   * Automatic: use this option if you want Veeam Backup & Replication to choose the backup proxy that will process object storage. * SelectedProxy: use this option if you want to specify the backup proxy that will process object storage. | VBRNASProxyMode | False | Named | False |
| SelectedProxyServer | For the SelectedProxy option of the ProxyMode parameter.  Specifies the backup proxy. Veeam Backup & Replication will use this backup proxy to to back up S3 compatible object storage. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from object storage. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRUnstructuredBackupIOControlLevel | False | Named | False |
| BucketName | Specifies a name of the S3 compatible bucket. The cmdlet will connect to this bucket. | String | False | Named | False |
| Force | Defines that the cmdlet will add S3 compatible object storage without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRS3CompatibleServer object that contains settings of S3 compatible storage added to the inventory.

Examples

Adding S3 Compatible Storage as Unstructured Data Source

This example shows how to add S3 compatible storage as unstructured data source to the inventory.

|  |
| --- |
| $account = Get-VBRAmazonAccount -AccessKey "XXXXXXXX" -Description "S3 account"  $cacherepository = Get-VBRBackupRepository -Name "WinSrv"  Add-VBRS3CompatibleServer -FriendlyName "S3 compatible" -Account $account -ServicePoint "S3.eu.compatible" -CacheRepository $cacherepository |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the AccessKey and Description parameters values. Save the result to the $account variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $cacherepository variable.
3. Run the Add-VBRAmazonS3Server cmdlet. Specify the following settings:

* Specify the FriendlyName parameter value.
* Set the $account variable as the Account parameter value.
* Specify the ServicePoint parameter value.
* Set the $cacherepository variable as the CacheRepository parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


