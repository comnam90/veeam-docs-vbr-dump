---
title: "Add-VBRAmazonS3CompatibleRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbramazons3compatiblerepository.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Add-VBRAmazonS3CompatibleRepository


Short Description

Adds S3 compatible and S3-integrated object storage repositories to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAmazonS3CompatibleRepository -AmazonS3Folder <VBRAmazonS3Folder> -Connection <VBRAmazonS3CompatibleConnection> [-Name <string>] [-Description <string>] [-EnableSizeLimit] [-SizeLimit <int>] [-EnableBackupImmutability] [-ImmutabilityPeriod <int>] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-MountServerOptions <VBRRepositoryMountServerOptions>] [-ProxyAppliance <CHost>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <int>] [-ForceOwnershipChange] [-EnableBucketAutoProvision] [-MachinesPerBucketLimit <Int32>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet adds S3 compatible and S3-integrated object storage repositories to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| AmazonS3Folder | Specifies an S3 compatible folder. Veeam Backup & Replication will store backup files in this folder. | Accepts the VBRAmazonS3Folder object. To get this object, run the [Get-VBRAmazonS3Folder](get-vbramazons3folder.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies an active session with S3 compatible object storage. The cmdlet will add it as a backup repository. | Accepts the VBRAmazonS3CompatibleConnection object. To get this object, run the [Connect-VBRAmazonS3CompatibleService](connect-vbramazons3compatibleservice.md) cmdlet and set the CapacityTier property as the ServiceType parameter value. | True | Named | False |
| Name | Specifies a name of an S3 compatible object storage. The cmdlet will add object storage with this name. | String | False | Named | False |
| Description | Specifies a description of an S3 compatible object storage. The cmdlet will add object storage with this description. | String | False | Named | False |
| EnableSizeLimit | Defines that the cmdlet will enable size limits for data blocks that you want to store in an S3 compatible storage.  Use the SizeLimit parameter to specify the size limits.  Default: False. | SwitchParameter | False | Named | False |
| SizeLimit | For the EnableSizeLimit parameter.  Specifies size limits in GB for data blocks that you want to store in an S3 compatible object storage added as a backup repository.  Permitted value: 1024 - 1073741824.  Default: 10240.  Note: [For S3-integrated repository] If you specify size limits that exceed an actual capacity of the S3-integrated repository, you will get a warning. Provide the Force parameter to skip this warning. | Int32 | False | Named | False |
| EnableIAStorageClass | Defines that the cmdlet will enable the infrequent access storage class for data blocks that are stored in an Amazon S3 object storage.  Default: False. | SwitchParameter | False | Named | False |
| EnableOZIAStorageClass | Defines that the cmdlet will enable the One Zone-IA storage class for data blocks that are stored in an Amazon S3 object storage.  Default: False. | SwitchParameter | False | Named | False |
| EnableBackupImmutability | Defines that the cmdlet will enable the immutability option.  Default: False. | SwitchParameter | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | For the EnableBackupImmutability parameter.  Defines the immutability period in days.  Default: 30 days.  Maximum: 999 days. | Int32 | False | Named | False |
| MountServerOptions | Specifies settings of a mount server for object storage repositories.  Note: This parameter is required for object storage repositories that you want to add as performance extents to a scale-out backup repository. | Accepts the VBRRepositoryMountServerOptions object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| ProxyAppliance | Specifies a helper appliance. Veeam Backup & Replication will use this appliance to perform a health check of backup files and apply retention to file backup job files. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByPropertyName) |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks paramter to specify the number of tasks.  Default: False. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by the object storage repository. | Int | False | Named | False |
| ForceOwnershipChange | Defines that the cmdlet will force ownership change of the object storage folder.  If you do not provide this parameter and the object storage folder is owned by another host, you will not be able to add object storage to the backup infrastructure.  Default: False. | SwitchParameter | False | Named | False |
| EnableBucketAutoProvision | For creating multiple child buckets.  Defines that the cmdlet will create multiple child buckets automatically. | SwitchParameter | False | Named | False |
| MachinesPerBucketLimit | For creating multiple child buckets.  Specifies a number of per-machine backup chains in a sub bucket. The cmdlet will create child buckets according to the amount of per-machine backup chains.  Default: 10. | Int32 | False | Named | False |
| Force | Defines that the cmdlet will add an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonS3CompatibleRepository](vbramazons3compatiblerepository.md)

Examples

Adding Amazon S3 Object Storage to Backup Infrastructure

This example shows how to add an Amazon S3 compatible object storage repository to the backup infrastructure.

|  |
| --- |
| $account = Get-VBRAmazonAccount  $connect = Connect-VBRAmazonS3CompatibleService -Account $account -CustomRegionId "us-east-1" -ServicePoint "http://123.45.67.89:9000"  $bucket = Get-VBRAmazonS3Bucket -Connection $connect -Name "New Bucket"  $folder = Get-VBRAmazonS3Folder -Name "New Folder" -Bucket $bucket -Connection $connect  Add-VBRAmazonS3CompatibleRepository -AmazonS3Folder $folder -Connection $connect -Name "New Repository" |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Save the result to the $account variable.
2. Run the [Connect-VBRAmazonS3CompatibleService](connect-vbramazons3compatibleservice.md) cmdlet. Set the $account variable as the Account parameter value. Specify the CustomRegionId and ServicePoint parameter values. Save the result to the $connect variable.
3. Run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. Set the $connect variable as the Connection parameter value. Specify the Name parameter value. Save the result to the $bucket variable.
4. Run the [Get-VBRAmazonS3Folder](get-vbramazons3folder.md) cmdlet. Specify the Name parameter value. Set the $bucket variable as the Bucket parameter value. Set the $connect variable as the Connection parameter value. Save the result to the $folder variable.
5. Run the Add-VBRAmazonS3CompatibleRepository cmdlet. Set the $folder variable as the AmazonS3Folder parameter value. Set the $connect variable as the Connection parameter value. Specify the Name parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3CompatibleService](connect-vbramazons3compatibleservice.md)
* [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md)
* [Get-VBRAmazonS3Folder](get-vbramazons3folder.md)


