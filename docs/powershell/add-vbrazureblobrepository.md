---
title: "Add-VBRAzureBlobRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrazureblobrepository.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRAzureBlobRepository

In this article

Short Description

Adds Azure Blob object storage repository to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAzureBlobRepository -Connection <VBRAzureBlobConnection> [-Name <String>] [-Description <String>] -AzureBlobFolder <VBRAzureBlobFolder>[-EnableSizeLimit] [-SizeLimit <Int32>] [-EnableCoolAccessTier] [-EnableBackupImmutability] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-ImmutabilityPeriod <Int32>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-AzureProxySpec <VBRAzureComputeProxyAppliance>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-ForceOwnershipChange] [-Force]  [<CommonParameters>]>] |

Detailed Description

This cmdlet adds Azure Blob object storage repository to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| AzureBlobFolder | Specifies an Azure Blob folder. The cmdlet will map object storage repository to this folder. | Accepts the VBRAzureBlobFolder object. To create this object, run the [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies an active session with Azure Blob storage that you want to add as the backup repository. | Accepts the VBRAzureBlobConnection object. To get this object, run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet and set the CapacityTier property as the ServiceType parameter value. | True | Named | False |
| Name | Specifies a name of an object storage. The cmdlet will add Azure Blob storage to the backup infrastructure with this name. | String | False | Named | False |
| Description | Specifies a description of Azure Blob storage. The cmdlet will add Azure Blob storage to the backup infrastructure with this description. | String | False | Named | False |
| EnableSizeLimit | Defines that the cmdlet will enable size limits for an Azure Blob storage that you want to add as a backup repository.  Use the SizeLimit parameter to specify the size limits. | SwitchParameter | False | Named | False |
| SizeLimit | For the EnableSizeLimit parameter.  Specifies size limits in GB for data blocks that you want to store in Azure Blob storage that you want to add as an object storage repository.  Permitted value: 1024 - 1073741824.  Default: 10240. | Int32 | False | Named | False |
| EnableCoolAccessTier | Defines that Veeam Backup & Replication will keep blocks of data in the Cool access tier.  Default: False. | SwitchParameter | False | Named | False |
| EnableBackupImmutability | Defines that the cmdlet will enable the immutability option.  Default: False. | SwitchParameter | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | For the EnableBackupImmutability parameter.  Defines the immutability period in days.  Default: 30 days. | Int32 | False | Named | False |
| MountServerOptions | Specifies settings of a mount server for object storage repositories.  Note: This parameter is required for object storage repositories that you want to add as performance extents to a scale-out backup repository. | Accepts the VBRRepositoryMountServerOptions object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks paramter to specify the number of tasks. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by the object storage repository. | Int32 | False | Named | False |
| AzureProxySpec | Specifies a helper appliance. Veeam Backup & Replication will use this appliance to perform a health check of backup files and apply retention to file backup job files. | Accepts the VBRAzureComputeProxyAppliance object. To create this object, run the [New-VBRAzureComputeProxyAppliance](new-vbrazurecomputeproxyappliance.md) cmdlet. | False | Named | False |
| ForceOwnershipChange | Defines that the cmdlet will force ownership change of the object storage folder.  If you do not provide this parameter and the object storage folder is owned by another host, you will not be able to add object storage to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureBlobRepository](vbrazureblobrepository.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Microsoft Azure Object Storage [Mapping to Existing Folder]

|  |  |
| --- | --- |
| This example shows how to add Microsoft Azure Object Storage to the backup infrastructure and map object storage repository to an existing folder.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier  $container = Get-VBRAzureBlobContainer -Connection $connect  $folder = Get-VBRAzureBlobFolder -Container $container -Connection $connect  Add-VBRAzureBlobRepository -AzureBlobFolder $folder[3] -Connection $connect |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Specify the Account, RegionType and ServiceType parameter values. Save the result to the $connect variable. 3. Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Specify the Connection parameter value. Save the result to the $container variable. 4. Run the [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md) cmdlet. Specify the Container and Connection parameter values. Save the result to the $folder variable.   The Get-VBRAzureBlobFolder cmdlet will return an array of folders. Mind the ordinal number of the necessary folders (in our example, it is the fourth restore point in the array).   1. Run the Add-VBRAzureBlobRepository cmdlet. Set the $folder variable as the AzureBlobFolder parameter value. Set the $connect variable as the Connection parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Microsoft Azure Object Storage [Mapping to New Folder]

|  |  |
| --- | --- |
| This example shows how to add Microsoft Azure Object Storage to the backup infrastructure and map object storage repository to a new folder. The cmdlet will map object storage repository to the Images folder.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier  $container = Get-VBRAzureBlobContainer -Connection $connect  $folder = New-VBRAzureBlobFolder -Container $container -Connection $connect -Name "Images"  Add-VBRAzureBlobRepository -AzureBlobFolder $folder -Connection $connect |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Specify the Account, RegionType and ServiceType parameter values. Save the result to the $connect variable. 3. Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Specify the Connection parameter value. Save the result to the $container variable. 4. Run the [New-VBRAzureBlobFolder](new-vbrazureblobfolder.md) cmdlet. Specify the Container, Connection and Name parameter values. Save the result to the $folder variable. 5. Run the Add-VBRAzureBlobRepository cmdlet. Set the $folder variable as the AzureBlobFolder parameter value. Set the $connect variable as the Connection parameter value. |

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md)
* [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md)
* [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md)
* [New-VBRAzureBlobFolder](new-vbrazureblobfolder.md)

Page updated 7/7/2025

Page content applies to build 13.0.1.1071
