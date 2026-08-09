---
title: "Set-VBRAzureArchiveRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazurearchiverepository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRAzureArchiveRepository


Short Description

Modifies settings for Azure Archive repository added to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAzureArchiveRepository -Repository <VBRAzureArchiveRepository> [-Name <String>] [-Description <String>] [-AzureProxySpec <VBRAzureComputeProxyAppliance>] [-UseInstantRetrieval] [-UseGatewayServer] [-GatewayServer <CHost[]>] [-ConnectionType <VBRRepositoryConnectionType>] [-ImmutabilityMode <VBRRepositoryImmutabilityMode>] [-ImmutabilityPeriod <Int32>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the settings for an Azure Archive repository added to the backup infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Repository | Specifies an Azure Archive repository that you want to modify. | Accepts the VBRAzureArchiveRepository object. To get this object, run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Name | Specifies a new name for the Azure Archive repository. | String | False | Named | False |
| Description | Specifies a new description of the Azure Archive repository. | String | False | Named | False |
| AzureProxySpec | Specifies a proxy appliance for transferring the data. | Accepts the VBRAzureComputeProxyAppliance object. To create this object, run the [New-VBRAzureComputeProxyAppliance](new-vbrazurecomputeproxyappliance.md) cmdlet. | False | Named | False |
| UseGatewayServer | Note: This parameter is deprecated and will be ignored. Use the GatewayServer parameter instead.  Defines that the cmdlet will use a gateway server to transfer data from processed VM to object storage repositories.  Default: False. | SwitchParameter | False | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories. Note: Provide the GatewayServer parameter to specify the server.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |
| UseInstantRetrieval | Defines that the cmdlet will create a repository where data blocks are marked with the cool access tier.  Note: If you do not provide the UseInstantRetrieval parameter, the cmdlet will create a repository where blocks are marked as the archive access tier.  Default: False. | SwitchParameter | False | Named | False |
| ImmutabilityMode | Specifies the immutability retention period:   * BackupRetention: Use this option if you want the immutability period to depend on the backup job retention. * RepositoryRetention: Use this option if you want to ignore the job retention and specify the immutability period explicitly. | VBRRepositoryImmutabilityMode | False | Named | False |
| ImmutabilityPeriod | Defines the immutability period in days.  Default: 30 days.  Maximum: 999 days. | Int32 | False | Named | False |
| Force | Defines that the cmdlet will modify an object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns VBRAzureArchiveRepository object that defines the Azure Archive repository settings.

Examples

Modifying Gateway Server of Azure Archive Repository

This example shows how to modify Azure Archive repository added to the backup infrastructure. The cmdlet will use custom gateway servers server to connect to Azure Archive repository.

|  |
| --- |
| $azure = Get-VBRArchiveObjectStorageRepository -Name "Azure"  $gateserv = Get-VBRServer -Name "north.tech.local", "north2.tech.local"  Set-VBRAzureArchiveRepository -Repository $azure -ConnectionType Gateway -GatewayServer $gateserv |

Perform the following steps:

1. Run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $azure variable.
2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $gateserv variable.
3. Run the Set-VBRAzureArchiveRepository cmdlet. Set the $azure variable as the Repository parameter value. Set the Gateway value for the ConnectionType parameter. Set the $gateserv variable as the GatewayServer parameter value.

Related Commands

* [Add-VBRAzureArchiveRepository](add-vbrazurearchiverepository.md)
* [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 2026-05-27

