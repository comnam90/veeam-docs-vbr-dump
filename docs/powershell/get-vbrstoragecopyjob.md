---
title: "Get-VBRStorageCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrstoragecopyjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRStorageCopyJob


Short Description

Returns storage backup copy jobs.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an array of storage backup copy jobs by the job name.

|  |
| --- |
| Get-VBRStorageCopyJob [-Name <String[]>] [<CommonParameters>] |

* Get storage backup copy jobs by the job ID.

|  |
| --- |
| Get-VBRStorageCopyJob [-Id <Guid>] [<CommonParameters>] |

Detailed Description

This cmdlet returns storage backup copy jobs for HPE StoreOnce and Dell Data Domain repositories.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Name | Specifies an array of names of storage backup copy jobs. The cmdlet will return the job with this name. | String[] | False | Named | False |
| Id | Specifies an ID of a storage backup copy job. The cmdlet will return the job with this ID. | Guid | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRStorageCopyJob object that contains settings of storage backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Backup Copy Job for HPE StoreOnce Repository by Name

|  |  |
| --- | --- |
| This command returns the StoreOnce copy job backup copy job for an HPE StoreOnce repository.  |  | | --- | | Get-VBRStorageCopyJob -Name "StoreOnce copy job" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Backup Copy Job for HPE StoreOnce Repositories by ID

|  |  |
| --- | --- |
| This command returns the cc20878e-614a-4e28-b00b-d2434bae15d7 backup copy job for an HPE StoreOnce repository.  |  | | --- | | Get-VBRStorageCopyJob -Id "cc20878e-614a-4e28-b00b-d2434bae15d7" | |

Page updated 2026-07-21

