---
title: "Add-VBRIBMCloudRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbribmcloudrepository.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# Add-VBRIBMCloudRepository

In this article

Short Description

Adds the IBM Cloud object storage repository to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRIBMCloudRepository -AmazonS3Folder <VBRAmazonS3Folder> -Connection <VBRAmazonS3CompatibleConnection> [-Name <String>] [-Description <String>] [-EnableSizeLimit] [-SizeLimit <Int32>] [-EnableBackupImmutability] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-ImmutabilityPeriod <Int32>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-ProxyAppliance <CHost>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-ForceOwnershipChange] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdelt adds the IBM Cloud object storage repository to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| AmazonS3Folder | Specifies an S3 compatible folder. Veeam Backup & Replication will store backup files in this folder. | Accepts the VBRAmazonS3Folder object. To get this object, run the [Get-VBRAmazonS3Folder](get-vbramazons3folder.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies an active session with S3 compatible object storage. The cmdlet will add it as a backup repository. | Accepts the VBRAmazonS3CompatibleConnection object. To get this object, run the [Connect-VBRAmazonS3CompatibleService](connect-vbramazons3compatibleservice.md) cmdlet and set the CapacityTier property as the ServiceType parameter value. | True | Named | False |
| Name | Specifies a name of an object storage repository. The cmdlet will add the object storage repository with this name. | String | False | Named | False |
| Description | Specifies a description of an object storage repository. The cmdlet will add the object storage repository with this description. | String | False | Named | False |
| EnableSizeLimit | Enables size limits for data blocks that you want to store in an object storage.  Use the SizeLimit parameter to specify the size limits.  Default: False. | SwitchParameter | False | Named | False |
| SizeLimit | For the EnableSizeLimit parameter.  Specifies size limits in GB for data blocks that you want to store in an object storage.  Permitted value: 1024 - 1073741824.  Default: 10240. | Int32 | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | Specifies the immutability period in days.  Default: 30. | Int32 | False | Named | False |
| MountServerOptions | Specifies settings of a mount server for object storage repositories.  Note: This parameter is required for object storage repositories that you want to add as performance extents to a scale-out backup repository. | Accepts the VBRRepositoryMountServerOptions object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| ProxyAppliance | Specifies a helper appliance. Veeam Backup & Replication will use this appliance to perform a health check of backup files and apply retention to file backup job files. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByPropertyName) |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks paramter to specify the number of tasks.  Default: False. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by the object storage repository. | Int | False | Named | False |
| ForceOwnershipChange | Defines that the cmdlet will force ownership change of the object storage folder.  If you do not provide this parameter and the object storage folder is owned by another host, you will not be able to add object storage to the backup infrastructure.  Default: False. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRIBMCloudRepository](vbribmcloudrepository.md)

Adding IBM Cloud Object Storage Repository to Backup Infrastructure

This example shows how to add the IBM Cloud object storage repository to the backup infrastructure. The repository will have the following settings:

* The object storage limits are enabled and are set to 1024 GB.
* The infrequent access storage class is enabled.

|  |
| --- |
| $account = Get-VBRAmazonAccount  $connect = Connect-VBRAmazonS3Service -Account $account[1] -RegionType Global -ServiceType CapacityTier  $bucket = Get-VBRAmazonS3Bucket -Connection $connect -Name "Bucket-01"  $folder = Get-VBRAmazonS3Folder -Name "bucket" -Bucket $bucket -Connection $connect  Add-VBRIBMCloudRepository -Name "IBM Cloud" -Connection $connect -AmazonS3Folder $folder -EnableSizeLimit -SizeLimit 1024 |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Save the result to the $account variable.
2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Specify the Account, RegionType and ServiceType parameter values. Save the result to the $connect variable.
3. Run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. Set the $connect variable as the Connection parameter value. Specify the Name parameter value. Save the result to the $bucket variable.
4. Run the [Get-VBRAmazonS3Folder](get-vbramazons3folder.md) cmdlet. Specify the Name parameter value. Set the $bucket variable as the Bucket parameter value. Set the $connect variable as the Connection parameter value. Save the result to the $folder variable.
5. Run the Add-VBRIBMCloudRepository cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the $connect variable as the Connection parameter value.
* Set the $folder variable as the AmazonS3Folder parameter value.
* Provide the EnableSizeLimit parameter.

* Provide the SizeLimit parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3Service](connect-vbramazons3service.md)
* [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md)
* [Get-VBRAmazonS3Folder](get-vbramazons3folder.md)

Page updated 9/5/2025

Page content applies to build 13.0.1.1071
