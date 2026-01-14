---
title: "Get-VBRAzureBlobAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureblobaccount.html"
last_updated: "2/19/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureBlobAccount

In this article

Short Description

Returns Microsoft Azure Blob credentials records.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Microsoft Azure Blob credentials records by the credentials records name.

|  |
| --- |
| Get-VBRAzureBlobAccount [-Name <string[]>]  [<CommonParameters>] |

* Get Microsoft Azure Blob credentials records by the credentials records ID.

|  |
| --- |
| Get-VBRAzureBlobAccount -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of credentials records for Microsoft Azure Blob storage added to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for Microsoft Azure Blob credentials records. The cmdlet will return Microsoft Azure Blob credentials records with these IDs. | Guid[] | True | Named | False |
| Name | Specifies an array of login names for Microsoft Azure Blob credentials records. The cmdlet will return Microsoft Azure Blob credentials records with these logins. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAzureBlobAccount object that contains Microsoft Azure Blob credentials records.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Microsoft Azure Blob Credentials Records by Name

|  |  |
| --- | --- |
| This command gets an Microsoft Azure Blob credentials record by the credentials record login name.  |  | | --- | | Get-VBRAzureBlobAccount -Name "Azure Blob" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Microsoft Azure Blob Credentials Records by ID

|  |  |
| --- | --- |
| This command gets an Microsoft Azure Blob credentials record by the credentials record ID.  |  | | --- | | Get-VBRAzureBlobAccount -Id "936edf7c-7cf3-4ddc-9895-c7485ef4bb2c" | |

Page updated 2/19/2024

Page content applies to build 13.0.1.1071
