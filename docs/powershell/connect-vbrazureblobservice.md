---
title: "Connect-VBRAzureBlobService"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbrazureblobservice.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# Connect-VBRAzureBlobService

In this article

Short Description

Connects to Microsoft Azure Blob storage.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Connect-VBRAzureBlobService -Account <VBRAzureBlobAccount> -RegionType <VBRAzureBlobRegionType> -ServiceType <VBRAzureServiceType> [-GatewayServer <CHost[]>] [-ConnectionType <VBRRepositoryConnectionType>]  [<CommonParameters>] |

Detailed Description

This cmdlet connects to Microsoft Azure Blob storage. It creates the VBRAzureBlobConnection object that contains connection settings that Veeam Backup & Replication will use to connect to Microsoft Azure Blob storage. You can use these settings to add Microsoft Azure Blob storage to the backup infrastructure as the following types of repositories:

* An object storage repository.
* An external repository. Run the [Add-VBRAzureExternalRepository](add-vbrazureexternalrepository.md) cmdlet to add to add Azure Blob storage as an external repository.
* A capacity extent of a scale-out backup repository.
* An archive extent of a scale-out backup repository.

|  |
| --- |
| Note |
| Consider the following:   * It is recommended to disconnect the Microsoft Azure Blob session at the end. Otherwise, the information that you get within the session will not be refreshed when you connect again, and outdated data will be used then. Run the [Disconnect-VBRAzureBlobService](disconnect-vbrazureblobservice.md) cmdlet to stop the session. * To get the current session, save the result that you get after you run the Connect-VBRAzureBlobService cmdlet to a variable. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies a Microsoft Azure Blob credentials record. The cmdlet will use this credentials record to connect to Microsoft Azure Blob storage. | Accepts the VBRAzureBlobAccount object. To get this object, run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. | True | Named | True (ByValue) |
| RegionType | Specifies the region type of Microsoft Azure Blob storage. The cmdlet will connect to the selected region type and will set up a connection with Microsoft Azure Blob storage. You can select the following types of regions:   * Global * Government * China   Note: If you use Microsoft Azure Blob storage to connect to Veeam Data Cloud Vault, you must provide the Global region. | String | True | Named | False |
| ServiceType | Specifies the type of the backup repository. The cmdlet will add the object storage as the specified type of the backup repository to the backup infrastructure.   * ExternalRepository: Use this option to add object storage as an external backup repository. * CapacityTier: Use this option to add object storage as a capacity extent or an object storage repository. * ArchiveTier: Use this option to add object storage as an archive extent. | VBRAzureServiceType | True | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRAzureBlobService object that contains connection settings for Microsoft Azure Blob storage.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Connecting to Microsoft Azure Blob Storage [External Repository Scenario]

|  |  |
| --- | --- |
| This example shows how to connect to Microsoft Azure Blob storage. Veeam Backup & Replication will use this connection to configure an external repository.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Microsoft Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType ExternalRepository |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the Connect-VBRAzureBlobService cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value. * Set the Global option for the RegionType parameter. * Set the ExternalRepository option for the ServiceType parameter. * Save the result to the $connect variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Connecting to Microsoft Azure Blob Storage [Capacity Extent Scenario]

|  |  |
| --- | --- |
| This example shows how to connect to Microsoft Azure Blob storage. Veeam Backup & Replication will use this connection type to configure a capacity extent of a scale-out backup repository.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Microsoft Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the Connect-VBRAzureBlobService cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value. * Set the Global option for the RegionType parameter. * Set the CapacityTier option for the ServiceType parameter. * Save the result to the $connect variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Connecting to Microsoft Azure Blob Storage Using Specific Gateway Server

|  |  |
| --- | --- |
| This example shows how to connect to Microsoft Azure Blob storage. Veeam Backup & Replication will use the North.tech.local gateway server to connect to Microsoft Azure Blob storage.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Microsoft Azure Blob"  $gate = Get-VBRServer -Name "North.tech.local"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -GatewayServer $gate |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $gate variable. 3. Run the Connect-VBRAzureBlobService cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value. * Set the Global option for the RegionType parameter. * Set the $gate variable as the GatewayServer parameter value. * Save the result to the $connect variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Connecting to Microsoft Azure Blob Storage [Archive Extent Scenario]

|  |  |
| --- | --- |
| This example shows how to connect to Microsoft Azure Blob storage. Veeam Backup & Replication will use this connection type to configure an archive extent of a scale-out backup repository.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Microsoft Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType ArchiveTier |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the Connect-VBRAzureBlobService cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value. * Set the Global option for the RegionType parameter. * Set the ArchiveTier option for the ServiceType parameter. * Save the result to the $connect variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Connecting to Microsoft Azure Blob Storage [Object Storage Repository Scenario]

|  |  |
| --- | --- |
| This example shows how to connect to Microsoft Azure Blob storage. Veeam Backup & Replication will use this connection type to configure an object storage repository.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Microsoft Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the Connect-VBRAzureBlobService cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value. * Set the Global option for the RegionType parameter. * Set the CapacityTier option for the ServiceType parameter. * Save the result to the $connect variable. |

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Get-VBRServer](get-vbrserver.md)

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
