---
title: "Connect-VBRAmazonS3Service"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbramazons3service.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Connect-VBRAmazonS3Service


Short Description

Connects to Amazon S3 object storage.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Connect-VBRAmazonS3Service -Account <VBRAmazonAccount> -RegionType <VBRAmazonRegionType> -ServiceType <VBRAmazonServiceType> [-GatewayServer <CHost[]>] [-ConnectionType <VBRRepositoryConnectionType>]  [<CommonParameters>] |

Detailed Description

This cmdlet connects to Amazon S3 object storage. It creates the IVBRAmazonS3Connection object that contains connection settings that Veeam Backup & Replication will use to connect to Amazon S3 object storage. You can use these settings to add Amazon S3 object storage to the backup infrastructure as the following types of repositories:

* An object storage repository.
* An external repository. Run the [Add-VBRAmazonS3ExternalRepository](add-vbramazons3externalrepository.md) cmdlet to add Amazon S3 as an external repository.
* A capacity extent of a scale-out backup repository.
* An archive extent of a scale-out backup repository.

|  |
| --- |
| Note |
| Consider the following:   * It is recommended to disconnect the Amazon S3 session at the end of the PowerShell session. Otherwise, the information that you get within the session will not be refreshed when you connect again, and outdated data will be used then. Run the [Disconnect-VBRAmazonS3Service](disconnect-vbramazons3service.md) cmdlet to stop the session.  * To get an active session, save the result that you get after you run the Connect-VBRAmazonS3Service cmdlet to a variable. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies an Amazon S3 credentials record. Veeam Backup & Replication will use this credentials record to connect to Amazon S3 object storage. | Accepts the [VBRAmazonAccount](vbramazonaccount.md) object. To create this object, run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. | True | Named | True (ByValue) |
| RegionType | Specifies the region type of Amazon S3 object storage. Veeam Backup & Replication will connect to the selected region type to set up a connection with Amazon S3 object storage. You can select the following types of regions:   * Global * Government * China | VBRAmazonRegionType | True | Named | False |
| ServiceType | Specifies the type of the backup repository. The cmdlet will add the object storage as the specified type of the backup repository to the backup infrastructure.   * ExternalRepository: Use this option to add object storage as an external backup repository. * CapacityTier: Use this option to add object storage as a capacity extent or an object storage repository. * ArchiveTier: Use this option to add object storage as an archive extent. | VBRAmazonServiceType | True | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonS3Connection](vbramazons3connection.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Connecting to Amazon S3 Object Storage [Capacity Extent Scenario]

|  |  |
| --- | --- |
| This example shows how to connect to Amazon S3 object storage. Veeam Backup & Replication will use this connection type to configure a capacity extent of a scale-out backup repository.  |  | | --- | | $account = Get-VBRAmazonAccount -AccessKey "XXXXXXXXXXXXXXX"  $connect = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $account variable. 2. Run the Connect-VBRAmazonS3Service cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value. * Set the Global option for the RegionType parameter. * Set the CapacityTier option for the ServiceType parameter.  * Save the result to the $connect variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Connecting to Amazon S3 Object Storage [External Repository Scenario]

|  |  |
| --- | --- |
| This example shows how to connect to Amazon S3 object storage. Veeam Backup & Replication will use this connection type to configure an external repository.  |  | | --- | | $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4ddc-9895-c7485ef4bb2c"  $connect = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType ExternalRepository |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.  1. Run the Connect-VBRAmazonS3Service cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value.  * Set the Global option for the RegionType parameter. * Set the ExternalRepository option for the ServiceType parameter.  * Save the result to the $connect variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Connecting to Amazon S3 Object Storage [Archive Extent Scenario]

|  |  |
| --- | --- |
| This example shows how to to connect to Amazon S3 object storage. Veeam Backup & Replication will use this connection type to set up an archive extent of a scale-out backup repository.  |  | | --- | | $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4ddc-9895-c7485ef4bb2c"  $connect = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType ArchiveTier |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.  1. Run the Connect-VBRAmazonS3Service cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value.  * Set the Global option for the RegionType parameter. * Set the ArchiveTier option for the ServiceType parameter. * Save the result to the $connect variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Connecting to Amazon S3 Object Storage [Object Storage Repository Scenario]

|  |  |
| --- | --- |
| This example shows how to connect to Amazon S3 object storage. Veeam Backup & Replication will use this connection type to configure an object storage repository.  |  | | --- | | $account = Get-VBRAmazonAccount -AccessKey "XXXXXXXXXXXXXXX"  $connect = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $account variable. 2. Run the Connect-VBRAmazonS3Service cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value.  * Set the Global option for the RegionType parameter. * Set the CapacityTier option for the ServiceType parameter.  * Save the result to the $connect variable. |

Related Commands

[Get-VBRAmazonAccount](get-vbramazonaccount.md)


