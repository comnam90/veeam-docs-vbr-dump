---
title: "Get-VBRCatalystCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcatalystcopyjob.html"
last_updated: "4/25/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCatalystCopyJob


Short Description

Returns backup copy jobs for HPE StoreOnce repositories.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an array of backup copy jobs for HPE StoreOnce repositories by the job name.

|  |
| --- |
| Get-VBRCatalystCopyJob -Name <string[]>  [<CommonParameters>] |

* Get backup copy jobs for HPE StoreOnce repositories by the job ID.

|  |
| --- |
| Get-VBRCatalystCopyJob -Id <guid>  [<CommonParameters>] |

Detailed Description

This cmdlet returns backup copy jobs for HPE StoreOnce repositories.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of backup copy jobs for HPE StoreOnce repositories. The cmdlet will return the job with this name. | String[] | True | Named | False |
| Id | Specifies an ID of a backup copy job for HPE StoreOnce repositories. The cmdlet will return the job with this ID. | Guid | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCatalystCopyJob object that contains settings of backup copy jobs for HPE StoreOnce repositories.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Backup Copy Job for HPE StoreOnce Repository by Name

|  |  |
| --- | --- |
| This command returns the StoreOnce copy job backup copy job for an HPE StoreOnce repository.  |  | | --- | | Get-VBRCatalystCopyJob -Name "StoreOnce copy job" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Backup Copy Job for HPE StoreOnce Repositories by ID

|  |  |
| --- | --- |
| This command returns the cc20878e-614a-4e28-b00b-d2434bae15d7 backup copy job for an HPE StoreOnce repository.  |  | | --- | | Get-VBRCatalystCopyJob -Id "cc20878e-614a-4e28-b00b-d2434bae15d7" | |


