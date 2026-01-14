---
title: "Set-VBRAzureDataBoxRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazuredataboxrepository.html"
last_updated: "4/15/2025"
product_version: "13.0.1.1071"
---

# Set-VBRAzureDataBoxRepository

In this article

Short Description

Modifies settings of Azure Data Box storage as an object storage repository to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAzureDataBoxRepository -Repository <VBRAzureDataBoxRepository> [-Name <String>] [-Description <String>] [-UseGatewayServer] [-ConnectionType <VBRRepositoryConnectionType>] [-GatewayServer <CHost[]>] [-EnableConcurrentTasksLimit] [-MaxConcurrentTasks <Int32>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies Azure Data Box storage that is added as an object storage repository to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies Azure Data Box storage that you want to modify. | Accepts the VBRAzureDataBoxRepository object. To get this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True |
| Name | Specifies a name of Azure Data Box storage. The cmdlet will add Azure Data Box storage to Veeam Backup & Replication with this name. | String | False | Named | False |
| Description | Specifies a description of Azure Data Box storage. The cmdlet will add Azure Data Box storage to Veeam Backup & Replication with this description. | String | False | Named | False |
| UseGatewayServer | Note: This parameter is deprecated and will be ignored. Use the GatewayServer parameter instead.  Defines that the cmdlet will use a gateway server to transfer data from processed VM to object storage repositories.  Default: False. | SwitchParameter | False | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |
| EnableConcurrentTasksLimit | Enables limits for concurrent tasks that can be processed by the object storage repository.  Use the MaxConcurrentTasks parameter to specify the number of tasks. | SwitchParameter | False | Named | False |
| MaxConcurrentTasks | To set maximum value for the LimitConcurrentJobs parameter.  Specifies the maximum allowed number of concurrent tasks for a repository.    Permitted values: 1 to 99. | Int32 | False | Named | False |
| Force | Defines that the cmdlet will modify an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureDataBoxRepository](vbrazuredataboxrepository.md)

Examples

Modifying Gateway Server for Azure Data Box Storage

This example shows how to modify Azure Data Box storage added as an object storage repository to the Veeam Backup & Replication infrastructure. The cmdlet will use custom gateway servers to connect to Azure Data Box storage.

|  |
| --- |
| $repository = Get-VBRObjectStorageRepository -Name "Azure Data Box"  $gateway = Get-VBRServer -Name "north.tech.local", "north2.tech.local"  Set-VBRAzureDataBoxRepository -Repository $repository -ConnectionType Gateway -GatewayServer $gateway |

Perform the following steps:

1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $gateway variable.
3. Run the Set-VBRAzureDataBoxRepository cmdlet. Set the $repository variable as the Repository parameter value. Set the Gateway value for the ConnectionType parameter. Set the $gateway variable as the GatewayServer parameter value.

Related Commands

* [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 4/15/2025

Page content applies to build 13.0.1.1071
