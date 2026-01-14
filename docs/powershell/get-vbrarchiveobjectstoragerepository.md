---
title: "Get-VBRArchiveObjectStorageRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrarchiveobjectstoragerepository.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Get-VBRArchiveObjectStorageRepository

In this article

Short Description

Returns archive repositories added to the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an array of all archive repositories added to Veeam Backup & Replication by their names.

|  |
| --- |
| Get-VBRArchiveObjectStorageRepository [-Name <string[]>] [-Type {AzureArchive | AmazonS3Glacier}]  [<CommonParameters>] |

* Get an array of archive repositories added to Veeam Backup & Replication by their IDs.

|  |
| --- |
| Get-VBRArchiveObjectStorageRepository [-Id <guid[]>] [-Type {AzureArchive | AmazonS3Glacier}]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of archive repositories added to Veeam Backup & Replication. You can get the following types of these archive repositories:

* Amazon S3 Glacier
* Azure Archive
* S3 compatible object storage with data archiving

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an ID of an archive repository that you want to get. | Guid | False | Named | False |
| Name | Specifies a name of an archive repository that you want to get. | String | False | Named | False |
| Type | Specifies the type of an archive repository that you want to get. You can select the following type of backup repositories:   * Amazon S3 Glacier * Azure Archive | Accepts the following types of objects:   * AzureArchive * AmazonS3Glacier   To create these objects, run the following cmdlets:   * [Add-VBRAzureArchiveRepository](add-vbrazurearchiverepository.md) * [Add-VBRAmazonS3GlacierRepository](add-vbramazons3glacierrepository.md) | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRArchiveObjectStorageRepository object that defines the archive repository settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Azure Archive Repositories

|  |  |
| --- | --- |
| This command gets all Azure Archive repository instances added to the backup infrastructure.  |  | | --- | | Get-VBRArchiveObjectStorageRepository -Type AzureArchive | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Amazon S3 Glacier Archive Repositories

|  |  |
| --- | --- |
| This command gets all Amazon S3 Glacier archive repository instances added to the backup infrastructure.  |  | | --- | | Get-VBRArchiveObjectStorageRepository -Type AmazonS3Glacier | |

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
