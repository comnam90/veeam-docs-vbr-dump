---
title: "Set-VBRGoogleCloudRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrgooglecloudrepository.html"
last_updated: "7/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRGoogleCloudRepository

In this article

Short Description

Modifies settings for Google Cloud object storage added to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRGoogleCloudRepository -Repository <VBRGoogleCloudRepository> [-Name <String>] [-Description <String>] [-UseGatewayServer] [-ConnectionType <VBRRepositoryConnectionType>] [-GatewayServer <CHost[]>] [-EnableSizeLimit] [-SizeLimit <Int32>] [-EnableNearlineStorageClass] [-EnableColdlineStorageClass] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-ImmutabilityPeriod <Int32>] [-MountServerOptions <VBRRepositoryMountServerOptions[]>] [-GoogleProxySpec <VBRGoogleCloudComputeProxyAppliance>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings for Google Cloud object storage added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies the Google Cloud object storage that you want to modify. | Accepts the VBRGoogleCloudRepository object. To create this object, run the [Add-VBRGoogleCloudRepository](add-vbrgooglecloudrepository.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Name | Specifies a name of Google Cloud object storage. The cmdlet will assign this name to Google Cloud object storage. | String | False | Named | False |
| Description | Specifies a description of Google Cloud object storage. The cmdlet will assign this description to Google Cloud object storage. | String | False | Named | False |
| UseGatewayServer | Note: This parameter is deprecated and will be ignored. Use the GatewayServer parameter instead.  Defines that the cmdlet will use a gateway server to transfer data from processed VM to object storage repositories.  Default: False. | SwitchParameter | False | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |
| EnableSizeLimit | Enables size limits for Google Cloud object storage that you want to add as an object storage.  Default: False.  Note: Use the SizeLimit parameter to specify the size limits. | SwitchParameter | False | Named | False |
| SizeLimit | For the EnableSizeLimit parameter.  Specifies the size limits in GB for data blocks that you want to store in Google Cloud object storage added as an object storage repository.  Permitted value: 1024 - 1073741824.  Default: 10240 GB. | Int | False | Named | False |
| EnableNearlineStorageClass | Assigns the Nearline storage class to data blocks that you want to keep in Google Cloud object storage. Use this option if you want to access data rarely (for example, once in a month or less) and plan to store data minimum 30 days.  Default: False.  Note: If you do not provide the EnableNearlineStorageClass or EnableColdlineStorageClass parameters, the cmdlet will assing the Standard storage class to data blocks. | SwitchParameter | False | Named | False |
| EnableColdlineStorageClass | Assigns the Coldline storage class to data blocks that you want to keep in Google Cloud object storage. Use this option if you plan to access your backup data rarely (for example, once a quarter) and plan to store data minimum 90 days.  Default: False.  Note: If you do not provide the EnableNearlineStorageClass or EnableColdlineStorageClass parameters, the cmdlet will assing the Standard storage class to data blocks. | SwitchParameter | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | Defines the immutability period in days.  Default: 30.  Maximum: 999. | Int32 | False | Named | False |
| MountServerOptions | Specifies settings of a mount server for object storage repositories.  Note: This parameter is required for object storage repositories that you want to add as performance extents to a scale-out backup repository. | Accepts the VBRRepositoryMountServerOptions object. To create this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | False | Named | False |
| GoogleProxySpec | Specifies proxy appliance settings. The cmdlet will use these settings to add Google Cloud object storage. | Accepts the VBRGoogleCloudComputeProxyAppliance object. To create this object, run the [New-VBRGoogleCloudComputeProxyAppliance](new-vbrgooglecloudcomputeproxyappliance.md) cmdlet. | False | Named | False |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by Google Cloud object storage.  Use the MaxConcurrentTasks paramter to specify the number of tasks. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | Specifies a maximum number of concurrent tasks that can be processed at once by Google Cloud object storage. | Int32 | False | Named | False |
| Force | Defines that the cmdlet will add Google Cloud object storage without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudRepository](vbrgooglecloudrepository.md)

Examples

Modifying Gateway Server of Google Cloud Object Storage

This example shows how to modify settings for a Google Cloud object storage added to the backup infrastructure. The cmdlet will use custom gateway servers to connect to Google Cloud object storage.

|  |
| --- |
| $repository = Get-VBRObjectStorageRepository -Name "google"  $gateserv = Get-VBRServer -Name "north.tech.local", "north2.tech.local"  Set-VBRGoogleCloudRepository -Repository $repository -ConnectionType Gateway -GatewayServer $gateserv |

Perform the following steps:

1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $gateserv variable.
3. Run the Set-VBRGoogleCloudRepository cmdlet. Set the $repository variable as the Repository parameter value. Set the Gateway value for the ConnectionType parameter. Set the $gateserv variable as the GatewayServer parameter value.

Related Commands

* [Add-VBRGoogleCloudRepository](add-vbrgooglecloudrepository.md)
* [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 7/7/2025

Page content applies to build 13.0.1.1071
