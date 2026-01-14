---
title: "Set-VBRDataCloudVaultRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrdatacloudvaultrepository.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRDataCloudVaultRepository

In this article

Short Description

Modifies a Veeam Data Cloud Vault added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRDataCloudVaultRepository -Repository <VBRDataCloudVaultRepository> [-Name <String>] [-Description <String>] [-ConnectionType <VBRRepositoryConnectionType>] [-GatewayServer <CHost[]>] [-EnableSizeLimit] [-SizeLimit <Int32>] [-ImmutabilityPeriod <Int32>] [-MountServerOptions <VBRRepositoryMountServerOptions>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a Veeam Data Cloud Vault added to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies a Veeam Data Cloud Vault that you want to modify. | Accepts the VBRAzureBlobRepository object. To get this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of an object storage repository. The cmdlet will assign this name to a Veeam Data Cloud Vault. | String | False | Named | False |
| Description | Specifies a description of an object repository. The cmdlet will assign this description to a Veeam Data Cloud Vault. | String | False | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| EnableSizeLimit | Defines that the cmdlet will enable size limits for an object storage repository.  Use the SizeLimit parameter to specify the size limits. | SwitchParameter | False | Named | False |
| SizeLimit | For the EnableSizeLimit parameter.  Specifies size limits in GB for data blocks that you want to store in an object storage repository.  Permitted value: 1024 - 1073741824.  Default: 10240. | Int32 | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | Defines the immutability period in days.  Default: 30.  Maximum: 999. | Int32 | False | Named | False |
| MountServerOptions | Specifies settings of a mount server for object storage repositories.  Note: This parameter is required for object storage repositories that you want to add as performance extents to a scale-out backup repository. | Accepts the VBRRepositoryMountServerOptions object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks paramter to specify the number of tasks. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by the object storage repository. | Int | False | Named | False |
| Force | Defines that the cmdlet will modify an storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDataCloudVaultRepository](vbrdatacloudvaultrepository.md)

Examples

Modifying Gateway Server Settings for Veeam Data Cloud Vault

This example shows how to modify settings for an existing Veeam Data Cloud Vault. The cmdlet will use custom gateway servers to transfer data to Veeam Data Cloud Vault.

|  |
| --- |
| $azure = Get-VBRObjectStorageRepository -Name "Azure Blob"  $gateserv = Get-VBRServer -Name "north.tech.local", "north2.tech.local"  Set-VBRDataCloudVaultRepository -Repository $azure -ConnectionType Gateway -GatewayServer $gateserv |

Perform the following steps:

1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $azure variable.
2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value Save the result to the $gateserv variable.
3. Run the Set-VBRAzureBlobRepository cmdlet. Set the $azure variable as the Repository parameter value. Set the Gateway value for the ConnectionType parameter. Set the $gateserv variable as the GatewayServer parameter value.

Related Commands

* [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 7/7/2025

Page content applies to build 13.0.1.1071
