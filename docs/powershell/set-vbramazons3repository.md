---
title: "Set-VBRAmazonS3Repository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbramazons3repository.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRAmazonS3Repository

In this article

Short Description

Modifies settings of Amazon S3 object storage added to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAmazonS3Repository -Repository <VBRAmazonS3Repository> [-Name <String>] [-Description <String>] [-EnableIAStorageClass] [-EnableOZIAStorageClass] [-UseGatewayServer] [-GatewayServer <CHost[]>] [-ConnectionType <VBRRepositoryConnectionType>] [-EnableSizeLimit] [-SizeLimit <Int32>] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-ImmutabilityPeriod <Int32>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-AmazonProxySpec <VBRAmazonEC2ProxyAppliance>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Amazon S3 object storage repository added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an Amazon S3 object storage that you want to modify. | Accepts the VBRAmazonS3Repository object. To create this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of an Amazon S3 object storage. The cmdlet will add object storage with this name. | String | False | Named | False |
| Description | Specifies a description of an Amazon S3 object storage. The cmdlet will add object storage with this description. | String | False | Named | False |
| EnableSizeLimit | Enables size limits for data blocks that you want to store in an Amazon S3 object storage.  Use the SizeLimit parameter to specify the size limits.  Default: False. | SwitchParameter | False | Named | False |
| SizeLimit | For the EnableSizeLimit parameter.  Specifies size limits in GB for data blocks that you want to store in an Amazon S3 object storage.  Permitted value: 1024 - 1073741824.  Default: 10240 GB. | Int32 | False | Named | False |
| EnableIAStorageClass | Defines that the cmdlet will enable the infrequent access storage class for data blocks that are stored in an Amazon S3 object storage.  Default: False. | SwitchParameter | False | Named | False |
| EnableOZIAStorageClass | Defines that the cmdlet will enable the One Zone-IA storage class for data blocks that are stored in an Amazon S3 object storage.  Default: False. | SwitchParameter | False | Named | False |
| UseGatewayServer | Note: This parameter is deprecated and will be ignored. Use the GatewayServer parameter instead.  Defines that the cmdlet will use a gateway server to transfer data from processed VM to object storage repositories.  Default: False. | SwitchParameter | False | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |
| ImmutabilityPeriod | For the EnableBackupImmutability parameter.  Defines the immutability period in days.  Default: 30. | Int32 | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| MountServerOptions | Specifies settings of a mount server for object storage repositories.  Note: This parameter is required for object storage repositories that you want to add as performance extents to a scale-out backup repository. | Accepts the VBRRepositoryMountServerOptions object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| AmazonProxySpec | Specifies a helper appliance. Veeam Backup & Replication will use this appliance to perform a health check of backup files and apply retention to file backup job files. | Accepts the VBRAmazonEC2ProxyAppliance object. To create this object, run the [New-VBRAmazonEC2ProxyAppliance](new-vbramazonec2proxyappliance.md) cmdlet. | False | Named | True (ByPropertyName) |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks paramter to specify the number of tasks.  Default: False. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by the object storage repository. | Int32 | False | Named | False |
| ForceOwnershipChange | Defines that the cmdlet will force ownership change of the object storage folder.  If you do not provide this parameter and the object storage folder is owned by another host, you will not be able to add object storage to the backup infrastructure.  Default: False. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will modify an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonS3Repository](vbramazons3repository.md)

Examples

Modifying Gateway Server Settings of Amazon S3 Object Storage

This example shows how to modify settings for an Amazon S3 object storage added as a backup repository. The cmdlet will use custom gateway servers to connect to Amazon S3 object storage.

|  |
| --- |
| $amazon = Get-VBRObjectStorageRepository -Name "Amazon S3"  $gateserv = Get-VBRServer -Name "north.tech.local", "north2.tech.local"  Set-VBRAmazonS3Repository -Repository $amazon -ConnectionType Gateway -GatewayServer $gateserv |

Perform the following steps:

1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $amazon variable.
2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $gateserv variable.
3. Run the Set-VBRAmazonS3Repository cmdlet. Set the $amazon variable as the Repository parameter value. Set the Gateway value for the ConnectionType parameter. Set the $gateserv variable as the GatewayServer parameter value.

Related Commands

* [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 7/7/2025

Page content applies to build 13.0.1.1071
