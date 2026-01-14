---
title: "Set-VBR1111SystemsS3Repository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbr1111systemss3repository.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBR1111SystemsS3Repository

In this article

Short Description

Modifies settings of the 11:11 Cloud object storage repository added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBR1111SystemsS3Repository -Repository <VBR1111SystemsS3Repository> [-Name <String>] [-Description <String>] [-EnableIAStorageClass] [-EnableOZIAStorageClass] [-UseGatewayServer] [-GatewayServer <CHost[]>] [-ConnectionType <VBRRepositoryConnectionType>] [-EnableSizeLimit] [-SizeLimit <Int32>] [-ImmutabilityPeriod <Int32>] [-MountServerOptions <VBRRepositoryMountServerOptions>] [-AmazonProxySpec <VBRAmazonEC2ProxyAppliance>] [-ProxyAppliance <CHost>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of the 11:11 Cloud object storage repository added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies the object storage repository that you want to modify. | Accepts the VBRAmazonS3Repository object. To create this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of an object storage repository. The cmdlet will use this name for the object storage repository. | String | False | Named | False |
| Description | Specifies a description of an object storage repository. The cmdlet will use this description for the object storage repository. | String | False | Named | False |
| EnableSizeLimit | Enables size limits for data blocks that you want to store in an object storage repository.  Use the SizeLimit parameter to specify the size limits.  Default: False. | SwitchParameter | False | Named | False |
| SizeLimit | For the EnableSizeLimit parameter.  Specifies size limits in GB for data blocks that you want to store in an object storage repository.  Permitted value: 1024 - 1073741824.  Default: 10240 GB. | Int32 | False | Named | False |
| EnableIAStorageClass | Defines that the cmdlet will enable the infrequent access storage class for data blocks that are stored in an object storage repository.  Default: False. | SwitchParameter | False | Named | False |
| UseGatewayServer | Note: This parameter is deprecated and will be ignored. Use the GatewayServer parameter instead.  Defines that the cmdlet will use a gateway server to transfer data from processed VM to object storage repositories.  Default: False. | SwitchParameter | False | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | For the EnableBackupImmutability parameter.  Defines the immutability period in days.  Default: 30. | Int32 | False | Named | False |
| MountServerOptions | Specifies settings of a mount server for object storage repositories.  Note: This parameter is required for object storage repositories that you want to add as performance extents to a scale-out backup repository. | Accepts the VBRRepositoryMountServerOptions object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| AmazonProxySpec | Specifies a helper appliance. Veeam Backup & Replication will use this appliance to perform a health check of backup files and apply retention to file backup job files. | Accepts the VBRAmazonEC2ProxyAppliance object. To create this object, run the [New-VBRAmazonEC2ProxyAppliance](new-vbramazonec2proxyappliance.md) cmdlet. | False | Named | True (ByPropertyName) |
| ProxyAppliance | Specifies a helper appliance. Veeam Backup & Replication will use this appliance to perform a health check of backup files and apply retention to file backup job files. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByPropertyName) |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks paramter to specify the number of tasks.  Default: False. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by the object storage repository. | Int32 | False | Named | False |
| ForceOwnershipChange | Defines that the cmdlet will force ownership change of the object storage folder.  If you do not provide this parameter and the object storage folder is owned by another host, you will not be able to add object storage to the backup infrastructure.  Default: False. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will modify an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBR1111SystemsS3Repository](vbr1111systemss3repository.md)

Examples

Modifying Gateway Server Settings of 11:11 Cloud Object Storage Repository

This example shows how to modify settings for the 11:11 cloud object storage repository. The cmdlet will use custom gateway servers to connect to 11:11 cloud object storage repository.

|  |
| --- |
| $1111systems = Get-VBRObjectStorageRepository -Name "11:11 Systems"  $gateserv = Get-VBRServer -Name "north.tech.local", "north2.tech.local"  Set-VBR1111SystemsS3Repository -Repository $1111systems -ConnectionType Gateway -GatewayServer $gateserv |

Perform the following steps:

1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $1111systems variable.
2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $gateserv variable.
3. Run the Set-VBR1111SystemsS3Repository cmdlet. Set the $1111systems variable as the Repository parameter value. Set the Gateway value for the ConnectionType parameter. Set the $gateserv variable as the GatewayServer parameter value.

Related Commands

* [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 7/7/2025

Page content applies to build 13.0.1.1071
