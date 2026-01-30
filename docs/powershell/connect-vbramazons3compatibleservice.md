---
title: "Connect-VBRAmazonS3CompatibleService"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbramazons3compatibleservice.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Connect-VBRAmazonS3CompatibleService


Short Description

Connects to S3 compatible object storage.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Connect-VBRAmazonS3CompatibleService -Account <VBRAmazonAccount> -CustomRegionId <string> -ServicePoint <string> [-ServiceType <VBRAmazonServiceType>] [-GatewayServer <CHost[]>] [-ConnectionType {Direct | Gateway}] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet connects to S3 compatible object storage. It creates the IVBRAmazonS3Connection object that contains the connection settings for the following types of storage:

* S3 compatible object storage
* S3 compatible object storage with data archiving
* AWS Snowball Edge device
* Wasabi Cloud Object Storage

You can use these settings to add S3 compatible devices to the backup infrastructure as the following types of repositories:

* An object storage repository. Run the [Add-VBRAmazonS3CompatibleRepository](add-vbramazons3compatiblerepository.md) cmdlet to add S3 compatible object storage as an object storage repository.
* An external repository. Run the [Add-VBRAmazonS3ExternalRepository](add-vbramazons3externalrepository.md) cmdlet to add S3 compatible as an external repository.
* A capacity extent of a scale-out backup repository.
* An archive extent of a scale-out backup repository.

|  |
| --- |
| Note |
| Consider the following:   * It is recommended to disconnect the S3 compatible session at the end. Otherwise, the information that you get within the session will not be refreshed when you connect again, and outdated data will be used then. Run the [Disconnect-VBRAmazonS3Service](disconnect-vbramazons3service.md) cmdlet to stop the session.  * To get an active session, save the result that you get after you run the Connect-VBRAmazonS3CompatibleService cmdlet to a variable. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies an S3 compatible service credentials record. Veeam Backup & Replication will use this credentials record to connect to S3 compatible object storage or S3 compatible object storage with data archiving. | Accepts the VBRAmazonAccount object. To create this object, run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. | True | Named | True (ByValue) |
| CustomRegionId | Specifies an Amazon S3 region where your S3 compatible object storage or or S3 compatible object storage with data archiving are located.  Note: To connect to the AWS Snowball Edge device, you must provide the snow value for the CustomRegionId parameter. | String | True | Named | False |
| ServicePoint | Specifies the endpoint. The cmdlet will use this endpoint to connect to S3 compatible object storage or S3 compatible object storage with data archiving. | String | True | Named | False |
| ServiceType | Specifies the type of the backup repository. The cmdlet will add the object storage as the specified type of the backup repository to the backup infrastructure.   * ExternalRepository: Use this option to add object storage as an external backup repository. * CapacityTier: Use this option to add object storage as a capacity extent or an object storage repository. * ArchiveTier: Use this option to add object storage as an archive extent. | String | False | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories.  Note: If you use S3 compatible service credentials records to connect to S3 compatible object storage with data archiving, the cmdlet will ignore these gateway server settings. It will use the settings that you specify for an archiver appliance. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |
| Force | Defines that the cmdlet will set up a connection to S3 compatible object storage even if Veeam Backup & Replication or Veeam Agent cannot validate that the certificate is issued from the trusted authorities. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonS3CompatibleRepository](vbramazons3compatiblerepository.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Connecting to S3 Compatible Object Storage

|  |  |
| --- | --- |
| This example shows how to connect to S3 compatible object storage.  |  | | --- | | $account = Get-VBRAmazonAccount -AccessKey "XXXXXXXXXXXXXXX"  Connect-VBRAmazonS3CompatibleService -Account $account -CustomRegionId "us-east-1" -ServicePoint "http://123.45.67.89:9000" |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $account variable. 2. Run the Connect-VBRAmazonS3CompatibleService cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value. * Specify the CustomRegionId parameter value. * Specify the ServicePoint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Connecting to AWS Snowball Edge

|  |  |
| --- | --- |
| This example shows how to connect to AWS Snowball Edge.  |  | | --- | | $account = Get-VBRAmazonAccount -AccessKey "XXXXXXXXXXXXXXX"  Connect-VBRAmazonS3CompatibleService -Account $account -CustomRegionId "snow" -ServicePoint "http://123.45.67.89:9000" |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $account variable.  1. Run the Connect-VBRAmazonS3CompatibleService cmdlet. Specify the following settings:  * Set the $account variable as the Account parameter value. * Specify the CustomRegionId parameter value. * Specify the ServicePoint parameter value. |

Related Commands

[Get-VBRAmazonAccount](get-vbramazonaccount.md)


