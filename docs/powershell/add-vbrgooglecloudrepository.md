---
title: "Add-VBRGoogleCloudRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrgooglecloudrepository.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRGoogleCloudRepository


Short Description

Adds the Google Cloud object storage repository to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRGoogleCloudRepository -Folder <VBRGoogleCloudFolder> -Connection <VBRGoogleCloudConnection> [-Name <String>] [-Description <String>] [-EnableSizeLimit] [-SizeLimit <Int32>] [-EnableNearlineStorageClass] [-EnableColdlineStorageClass] [-EnableBackupImmutability] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-ImmutabilityPeriod <Int32>] [-GoogleProxySpec <VBRGoogleCloudComputeProxyAppliance>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-ForceOwnershipChange] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds the Google Cloud object storage repository to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Folder | Specifies a Google Cloud folder. Veeam Backup & Replication will move backup files into this folder. | Accepts the VBRGoogleCloudFolder object. To create this object, run the [New-VBRGoogleCloudFolder](new-vbrgooglecloudfolder.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies an active session with a Google Cloud object storage that you want to add to the backup infrastructure. | Accepts the VBRGoogleCloudConnection object. To create this object, run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. | True | Named | False |
| Name | Specifies a name of the Google Cloud object storage. The cmdlet will add an object storage with this name. | String | False | Named | False |
| Description | Specifies a description of a Google Cloud object storage. The cmdlet will add an object storage with this description. | String | False | Named | False |
| EnableSizeLimit | Enables size limits for the Google Cloud storage that you want to add as an object storage.  Default: False.  Note: Use the SizeLimit parameter to specify the size limits. | SwitchParameter | False | Named | False |
| SizeLimit | For the EnableSizeLimit parameter.  Specifies the size limits in TB or PB for data blocks that you want to store in Google Cloud storage added as an object storage repository.  Default: 10 TB. | Int | False | Named | False |
| EnableNearlineStorageClass | Enables the nearline storage class for optimized archive storage.  Default: False. | SwitchParameter | False | Named | False |
| GoogleProxySpec | Specifies proxy appliance settings for adding object storage repository. | Accepts the VBRGoogleCloudComputeProxyAppliance object. To create this object, run the [New-VBRGoogleCloudComputeProxyAppliance](new-vbrgooglecloudcomputeproxyappliance.md) cmdlet. | False | Named | False |
| MountServerOptions | Specifies settings of a mount server for object storage repositories.  Note: This parameter is required for object storage repositories that you want to add as performance extents to a scale-out backup repository. | Accepts the VBRRepositoryMountServerOptions object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will add ab object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| EnableColdlineStorageClass | Enables the coldline storage class to data blocks that you want to keep in Google Cloud object storage. Use this option if you plan to access your backup data rarely (for example, once a quarter) and plan to store data minimum 90 days.  Default: False.  Note: If you do not provide the EnableNearlineStorageClass or EnableColdlineStorageClass parameters, the cmdlet will assing the Standard storage class to data blocks. | SwitchParameter | False | Named | False |
| EnableBackupImmutability | Defines that the cmdlet will enable the immutability option.  Default: False. | SwitchParameter | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | Defines the immutability period in days.  Default: 30.  Maximum: 999. | Int32 | False | Named | False |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks paramter to specify the number of tasks. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by the object storage repository. | Int | False | Named | False |
| ForceOwnershipChange | Defines that the cmdlet will force ownership change of the object storage folder.  If you do not provide this parameter and the object storage folder is owned by another host, you will not be able to add object storage to the backup infrastructure. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudRepository](vbrgooglecloudrepository.md)

Examples

Adding Google Cloud Repository

This example shows how to add Google Cloud object storage to the backup infrastructure.

|  |
| --- |
| $account = Get-VBRGoogleCloudAccount -AccessKey "XXXXXXXXXXXXXXXXXXX"  $connection = Connect-VBRGoogleCloudService -Account $account -ServiceType CapacityTier  $region = Get-VBRGoogleCloudRegion -Connection $connection  $bucket = Get-VBRGoogleCloudBucket -Connection $connection -Region $region -Name "bucket01"  $folder = Get-VBRGoogleCloudFolder -Connection $connection -Bucket $bucket -Name "veeam"  Add-VBRGoogleCloudRepository -Connection $connection -Folder $folder -Name "Repository09" |

Perform the following steps:

1. Specify Google Cloud connection settings:

1. Run the [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. Set the $account variable as the Account parameter value. Specify the ServiceType parameter value. Save the result to the $connection variable.

1. Specify object storage settings:

1. Run the [Get-VBRGoogleCloudRegion](get-vbrgooglecloudregion.md) cmdlet. Set the $connection variable as the Connection parameter value. Save the result to the $region variable.
2. Run the [Get-VBRGoogleCloudBucket](get-vbrgooglecloudbucket.md) cmdlet. Set the $connection variable as the Connection parameter value. Set the $region variable as the Region parameter value. Specify the Name parameter value. Save the result to the $bucket variable.
3. Run the [Get-VBRGoogleCloudFolder](get-vbrgooglecloudfolder.md) cmdlet. Set the $connection variable as the Connection parameter value. Set the $bucket variable as the Bucket parameter value. Specify the Name parameter value. Save the result to the $folder variable.

1. Run the Add-VBRGoogleCloudRepository cmdlet. Specify the following settings:

* Set the $connection variable as the Connection parameter value.
* Set the $folder variable as the Folder parameter value.
* Specify the Name parameter value.

Related Commands

* [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)
* [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md)
* [Get-VBRGoogleCloudRegion](get-vbrgooglecloudregion.md)
* [Get-VBRGoogleCloudBucket](get-vbrgooglecloudbucket.md)
* [Get-VBRGoogleCloudFolder](get-vbrgooglecloudfolder.md)


