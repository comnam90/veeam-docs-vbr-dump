---
title: "Set-VBRAmazonS3GlacierRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbramazons3glacierrepository.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAmazonS3GlacierRepository

In this article

Short Description

Modifies settings for Amazon S3 Glacier archive storage added as a backup repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAmazonS3GlacierRepository -Repository <VBRAmazonS3GlacierRepository> [-Name <String>] [-Description <String>] [-AmazonProxySpec <VBRAmazonEC2ProxyAppliance>] [-UseDeepArchive] [-UseInstantRetrieval] [-UseGatewayServer] [-GatewayServer <CHost[]>] [-ConnectionType <VBRRepositoryConnectionType>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings for Amazon S3 Glacier archive storage repository added as a backup repository.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an Amazons S3 Glacier archive storage that you want to modify. | Accepts the VBRAmazonS3GlacierRepository object. To get this object, run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of an Amazon S3 Glacier object storage. The cmdlet will add object storage with this name. | String | False | Named | False |
| Description | Specifies a description of an Amazon S3 Glacier object storage. The cmdlet will add object storage with this description. | String | False | Named | False |
| AmazonProxySpec | Specifies the archiver appliance that will transfer the data from Amazon S3 to Amazon S3 Glacier object storage. | Accepts the VBRAmazonEC2ProxyAppliance object. To create this object, run the [New-VBRAmazonEC2ProxyAppliance](new-vbramazonec2proxyappliance.md) cmdlet. | True | Named | True (ByPropertyName) |
| UseDeepArchive | Defines that the cmdlet will create a repository where blocks are marked with the Glacier Deep Archive storage class.  Note: If you do not provide the UseDeepArchive and UseInstantRetrieval parameters, the cmdlet will create a repository where blocks are marked as the Amazon S3 Glacier Flexible Retrieval storage class.    Default: False. | SwitchParameter | False | Named | False |
| UseInstantRetrieval | Defines that the cmdlet will create a repository where blocks are marked with the Amazon S3 Glacier Instant Retrieval storage class.  Note: If you do not provide the UseDeepArchive and UseInstantRetrieval parameters, the cmdlet will create a repository where blocks are marked as the Amazon S3 Glacier Flexible Retrieval storage class.    Default: False. | SwitchParameter | False | Named | False |
| UseGatewayServer | Note: This parameter is deprecated and will be ignored. Use the GatewayServer parameter instead.  Defines that the cmdlet will use a gateway server to transfer data from processed VM to object storage repositories.  Default: False. | SwitchParameter | False | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |
| Force | Defines that the cmdlet will modify object storage repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonS3GlacierRepository](vbramazons3glacierrepository.md)

Examples

Modifying Amazon S3 Glacier Storage Class

This example shows how to modify settings of the Repository 03 Amazon S3 Glacier object storage. The cmdlet will set the Glacier Deep Archive storage class to data blocks located in the object storage.

|  |
| --- |
| $amazon = Get-VBRArchiveObjectStorageRepository -Name "Repository 03"  Set-VBRAmazonS3GlacierRepository -Repository $amazon -UseDeepArchive |

Perform the following steps:

1. Run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $amazon variable.
2. Run the Set-VBRAmazonS3GlacierRepository cmdlet. Set the $amazon variable as the Repository parameter value. Provide the UseDeepArchive parameter.

Related Commands

* [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md)

* [Get-VBRServer](get-vbrserver.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
