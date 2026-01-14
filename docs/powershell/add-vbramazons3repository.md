---
title: "Add-VBRAmazonS3Repository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbramazons3repository.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRAmazonS3Repository

In this article

Short Description

Adds Amazon S3 object storage repository to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAmazonS3Repository -AmazonS3Folder <VBRAmazonS3Folder> -Connection <VBRAmazonS3Connection> [-Name <string>] [-Description <string>] [-EnableSizeLimit] [-SizeLimit <int>] [-EnableIAStorageClass] [-EnableOZIAStorageClass] [-EnableBackupImmutability] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-ImmutabilityPeriod <int>] [-MountServerOptions <VBRRepositoryMountServerOptions>] [-AmazonProxySpec <VBRAmazonEC2ProxyAppliance>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <int>] [-ForceOwnershipChange] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds Amazon S3 object storage repository to the backup infrastructure.

|  |
| --- |
| Important |
| Run the [Add-VBRAmazonS3ExternalRepository](add-vbramazons3externalrepository.md) to add Amazon S3 object storage as an external backup repository. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| AmazonS3Folder | Specifies an Amazon S3 folder. | Accepts the VBRAmazonS3Folder object. To get this object, run the [Get-VBRAmazonS3Folder](get-vbramazons3folder.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies an active session with Amazon S3 object storage that you want to add as the backup repository. | Accepts the VBRAmazonS3Connection object. To get this object, run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet and set the CapacityTier property as the ServiceType parameter value. | True | Named | False |
| Name | Specifies a name of an Amazon S3 object storage. The cmdlet will add object storage with this name. | String | False | Named | False |
| Description | Specifies a description of an Amazon S3 object storage. The cmdlet will add object storage with this description. | String | False | Named | False |
| EnableSizeLimit | Enables size limits for data blocks that you want to store in an Amazon S3 object storage.  Use the SizeLimit parameter to specify the size limits.  Default: False. | SwitchParameter | False | Named | False |
| SizeLimit | For the EnableSizeLimit parameter.  Specifies size limits in GB for data blocks that you want to store in an Amazon S3 object storage.  Permitted value: 1024 - 1073741824.  Default: 10240 GB. | Int32 | False | Named | False |
| EnableIAStorageClass | Defines that the cmdlet will enable the infrequent access storage class for data blocks that are stored in an Amazon S3 object storage.  Default: False. | SwitchParameter | False | Named | False |
| EnableOZIAStorageClass | Defines that the cmdlet will enable the One Zone-IA storage class for data blocks that are stored in an Amazon S3 object storage.  Default: False. | SwitchParameter | False | Named | False |
| EnableBackupImmutability | Defines that the cmdlet will enable the immutability option.  Default: False. | SwitchParameter | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | For the EnableBackupImmutability parameter.  Defines the immutability period in days.  Default: 30 | Int32 | False | Named | False |
| MountServerOptions | Specifies settings of a mount server for object storage repositories.  Note: This parameter is required for object storage repositories that you want to add as performance extents to a scale-out backup repository. | Accepts the VBRRepositoryMountServerOptions object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| AmazonProxySpec | Specifies a helper appliance. Veeam Backup & Replication will use this appliance to perform a health check of backup files and apply retention to file backup job files. | Accepts the VBRAmazonEC2ProxyAppliance object. To create this object, run the [New-VBRAmazonEC2ProxyAppliance](new-vbramazonec2proxyappliance.md) cmdlet. | False | Named | True (ByPropertyName) |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks paramter to specify the number of tasks.  Default: False. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by the object storage repository. | Int | False | Named | False |
| ForceOwnershipChange | Defines that the cmdlet will force ownership change of the object storage folder.  If you do not provide this parameter and the object storage folder is owned by another host, you will not be able to add object storage to the backup infrastructure.  Default: False. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonS3Repository](vbramazons3repository.md)

Examples

Adding Amazon S3 Object Storage to Backup Infrastructure

This example shows how to add Amazon S3 object storage as a backup repository to Veeam Backup & Replication. The repository will have the following settings:

* The object storage limits are enabled and are set to 1024 GB.
* The infrequent access storage class is enabled.

|  |
| --- |
| $account = Get-VBRAmazonAccount  $connect = Connect-VBRAmazonS3Service -Account $account[1] -RegionType Global -ServiceType CapacityTier  $bucket = Get-VBRAmazonS3Bucket -Connection $connect -Name "Bucket-01"  $folder = Get-VBRAmazonS3Folder -Name "bucket" -Bucket $bucket -Connection $connect  Add-VBRAmazonS3Repository -Name "AmazonS3Repository" -Connection $connect -AmazonS3Folder $folder -EnableIAStorageClass -EnableSizeLimit -SizeLimit 1024 |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Save the result to the $account variable.
2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Specify the Account, RegionType and ServiceType parameter values. Save the result to the $connect variable.
3. Run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. Set the $connect variable as the Connection parameter value. Specify the Name parameter value. Save the result to the $bucket variable.
4. Run the [Get-VBRAmazonS3Folder](get-vbramazons3folder.md) cmdlet. Specify the Name parameter value. Set the $bucket variable as the Bucket parameter value. Set the $connect variable as the Connection parameter value. Save the result to the $folder variable.
5. Run the Add-VBRAmazonS3Repository cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the $connect variable as the Connection parameter value.
* Set the $folder variable as the AmazonS3Folder parameter value.

* Provide the EnableIAStorageClass parameter.

* Provide the EnableSizeLimit parameter.

* Provide the SizeLimit parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3Service](connect-vbramazons3service.md)
* [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md)
* [Get-VBRAmazonS3Folder](get-vbramazons3folder.md)

Page updated 7/7/2025

Page content applies to build 13.0.1.1071
