---
title: "Add-VBRDataCloudVaultRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrdatacloudvaultrepository.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRDataCloudVaultRepository


Short Description

Adds a Veeam Data Cloud Vault to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a Veeam Data Cloud Vault using a subscription.

|  |
| --- |
| Important |
| Before you run this parameter set, you must assign a vault to your backup server. For more information, see the [Getting Started with Veeam Data Cloud Vault](https://helpcenter.veeam.com/docs/vdcv/userguide/getting_started.html) section in the Veeam Data Cloud Vault User Guide. |

|  |
| --- |
| Add-VBRDataCloudVaultRepository [-Name <String>] [-Description <String>] [-Vault <VBRVeeamDataCloudAssignedVault>] [-Folder <String>] [-GatewayServer <CHost[]>] [-ConnectionType <VBRRepositoryConnectionType>] [-EnableSizeLimit] [-SizeLimit <Int32>] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-ImmutabilityPeriod <Int32>] [-MountServerOptions <VBRRepositoryMountServerOptions>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-ForceOwnershipChange] [-Force] [<CommonParameters>] |

* Add a Veeam Data Cloud Vault using the service key.

|  |
| --- |
| Add-VBRDataCloudVaultRepository [-Name <String>] [-Description <String>] [-AzureBlobFolder <VBRAzureBlobFolder>] [-Connection <VBRAzureBlobConnection>] [-EnableSizeLimit] [-SizeLimit <Int32>] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-ImmutabilityPeriod <Int32>] [-MountServerOptions <VBRRepositoryMountServerOptions>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-ForceOwnershipChange] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet adds a Veeam Data Cloud Vault to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Vault | [Subscription scenario]  Specifies a Veeam storage vault assigned to the backup server. The cmdlet will add this vault to the backup infrastructure. | Accepts the [VBRVeeamDataCloudAssignedVault](vbrveeamdatacloudassignedvault.md) object. To get this object, run the [Get-VBRVeeamDataCloudAssignedVault](get-vbrveeamdatacloudassignedvault.md) cmdlet. | False | Named | False |
| Folder | [Subscription scenario]  Specifies the folder that will be used to store data. | String | False | Named | False |
| GatewayServer | [Subscription scenario]  Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ConnectionType | [Subscription scenario]  Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories. Note: Provide the GatewayServer parameter to specify the server.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |
| AzureBlobFolder | [Service key scenario]  Specifies an Azure Blob folder. The cmdlet will map Veeam Data Cloud Vault to this folder. | Accepts the VBRAzureBlobFolder object. To get this object, run the [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md) cmdlet. | False | Named | True (ByValue) |
| Connection | [Service key scenario]  Specifies an active session with Azure Blob storage. The cmdlet will use this connection to add a Veeam Data Cloud Vault. | Accepts the VBRAzureBlobConnection object. To get this object, run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet and set the CapacityTier property as the ServiceType parameter value. | False | Named | False |
| Name | Specifies a name of an object storage repository. The cmdlet will add a Veeam Data Cloud Vault to the backup infrastructure with this name. | String | False | Named | False |
| Description | Specifies a description of an object storage repository. The cmdlet will add a Veeam Data Cloud Vault to the backup infrastructure with this description. | String | False | Named | False |
| EnableSizeLimit | Defines that the cmdlet will enable size limits for a Veeam Data Cloud Vault that you want to add as a backup repository.  Use the SizeLimit parameter to specify the size limits. | SwitchParameter | False | Named | False |
| SizeLimit | For the EnableSizeLimit parameter.  Specifies size limits in GB for data blocks that you want to store in a Veeam Data Cloud Vault.  Permitted value: 1024 - 1073741824.  Default: 10240. | Int32 | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | Defines the immutability period in days.  Default: 30.  Maximum: 999. | Int32 | False | Named | False |
| MountServerOptions | Specifies settings of a mount server for object storage repositories.  Note: This parameter is required for object storage repositories that you want to add as performance extents to a scale-out backup repository. | Accepts the VBRRepositoryMountServerOptions object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks paramter to specify the number of tasks. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by the object storage repository. | Int32 | False | Named | False |
| ForceOwnershipChange | Defines that the cmdlet will force ownership change of the object storage folder.  If you do not provide this parameter and the object storage folder is owned by another host, you will not be able to add object storage to the backup infrastructure. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will add an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDataCloudVaultRepository](vbrdatacloudvaultrepository.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Veeam Data Cloud Vault [Using Subscription]

|  |  |
| --- | --- |
| This example shows how to add Veeam Data Cloud Vault to the backup infrastructure using a subscription.  |  | | --- | | $vault = Get-VBRVeeamDataCloudAssignedVault  $gateway = Get-VBRServer  Add-VBRDataCloudVaultRepository -Name "Vault2049" -Description "New Vault" -Vault $vault -Folder "Backups" -GatewayServer $gateway -ConnectionType Direct -ImmutabilityPeriod 14 |  Perform the following steps:   1. Run the [Get-VBRVeeamDataCloudAssignedVault](get-vbrveeamdatacloudassignedvault.md) cmdlet. Save the result to the $vault variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $gateway variable. 3. Run the Add-VBRDataCloudVaultRepository cmdlet. Specify the following settings:  * Specify the Name parameter value. * Specify the Description parameter value. * Set the $vault variable as the Vault parameter value. * Specify the Folder parameter value. * Set the $gateway variable as the GatewayServer parameter value. * Specify the ConnectionType parameter value. * Specify the ImmutabilityPeriod parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Veeam Data Cloud Vault using Service Key [Mapping to Existing Folder]

|  |  |
| --- | --- |
| This example shows how to add Veeam Data Cloud Vault to the backup infrastructure using a service key, and map object storage repository to an existing folder.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier  $container = Get-VBRAzureBlobContainer -Connection $connect  $folder = Get-VBRAzureBlobFolder -Container $container -Connection $connect  Add-VBRDataCloudVaultRepository -AzureBlobFolder $folder[3] -Connection $connect |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Specify the Account, RegionType and ServiceType parameter values. Save the result to the $connect variable.   Note: You must specify the Global region to use a connection with Azure Blob storage and add a Veeam Data Cloud Vault.   1. Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Specify the Connection parameter value. Save the result to the $container variable. 2. Run the [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md) cmdlet. Specify the Container and Connection parameter values. Save the result to the $folder variable.   The Get-VBRAzureBlobFolder cmdlet will return an array of folders. Mind the ordinal number of the necessary folders (in our example, it is the fourth restore point in the array).   1. Run the Add-VBRDataCloudVaultRepository cmdlet. Set the $folder variable as the AzureBlobFolder parameter value. Set the $connect variable as the Connection parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding Veeam Data Cloud Vault [Mapping to New Folder]

|  |  |
| --- | --- |
| This example shows how to add Veeam Data Cloud Vault to the backup infrastructure and map object storage repository to a new folder. The cmdlet will map object storage repository to the Images folder.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier  $container = Get-VBRAzureBlobContainer -Connection $connect  $folder = New-VBRAzureBlobFolder -Container $container -Connection $connect -Name "Images"  Add-VBRDataCloudVaultRepository -AzureBlobFolder $folder -Connection $connect |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Specify the Account, RegionType and ServiceType parameter values. Save the result to the $connect variable. 3. Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Specify the Connection parameter value. Save the result to the $container variable. 4. Run the [New-VBRAzureBlobFolder](new-vbrazureblobfolder.md) cmdlet. Specify the Container, Connection and Name parameter values. Save the result to the $folder variable. 5. Run the Add-VBRDataCloudVaultRepository cmdlet. Set the $folder variable as the AzureBlobFolder parameter value. Set the $connect variable as the Connection parameter value. |

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md)
* [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md)
* [Get-VBRAzureBlobFolder](get-vbrazureblobfolder.md)
* [New-VBRAzureBlobFolder](new-vbrazureblobfolder.md)


