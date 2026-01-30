---
title: "Get-VBRObjectStorageRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrobjectstoragerepository.html"
last_updated: "11/22/2024"
product_version: "13.0.1.1071"
---

# Get-VBRObjectStorageRepository


Short Description

Returns object storage added as backup repositories to Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an array of all object storage added as backup repositories from Veeam Backup & Replication.

|  |
| --- |
| Get-VBRObjectStorageRepository [-Name <string[]>] [-Type {AmazonS3 | AmazonS3Compatible | AzureBlob | AzureDataBox | GoogleCloudStorage | Wasabi | DataCloudVault | ElevenEleven]  [<CommonParameters>] |

* Get an array of object storage added as backup repositories by the backup repositories IDs.

|  |
| --- |
| Get-VBRObjectStorageRepository -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of object storage added as backup repositories to Veeam Backup & Replication. You can get the following types of these backup repositories:

* Amazon S3
* S3 compatible
* Azure Blob
* Azure Data Box
* Google Cloud
* Wasabi Cloud Storage
* Veeam Data Cloud Vault
* 11:11 Cloud Object Storage to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an ID of a backup repository that you want to get. | Guid[] | True | Named | False |
| Name | Specifies the name of a backup repository that you want to get. | String[] | False | Named | False |
| Type | Specifies the type of a backup repository that you want to get. You can select the following type of backup repositories:   * AmazonS3 * AmazonS3Compatible * AzureBlob * AzureDataBox * GoogleCloudStorage * Wasabi * DataCloudVault * ElevenEleven | [VBRObjectStorageRepositoryType](enums.md#VBRObjectStorageRepositoryType) | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRObjectStorageRepository object containing an array of object storage added as backup repositories to Veeam Backup & Replication.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Microsoft Azure Blob Object Storage

|  |  |
| --- | --- |
| This command gets all Azure Blob storage added as backup repositories.  |  | | --- | | Get-VBRObjectStorageRepository -Type AzureBlob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Amazon S3 Object Storage

|  |  |
| --- | --- |
| This command gets all Amazon S3 object storage added as backup repositories.  |  | | --- | | Get-VBRObjectStorageRepository -Type AmazonS3 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All S3 Compatible Object Storage

|  |  |
| --- | --- |
| This command gets all S3 compatible object storage added as backup repositories.  |  | | --- | | Get-VBRObjectStorageRepository -Type AmazonS3Compatible | |


