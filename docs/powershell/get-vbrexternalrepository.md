---
title: "Get-VBRExternalRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrexternalrepository.html"
last_updated: "1/30/2024"
product_version: "13.0.1.1071"
---

# Get-VBRExternalRepository


Short Description

Returns an array of external repositories from the backup infrastructure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an external repository by the external repository ID.

|  |
| --- |
| Get-VBRExternalRepository -Id <guid[]>  [<CommonParameters>] |

* Get an external repository by the external repository name.

|  |
| --- |
| Get-VBRExternalRepository [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of external repositories added to the backup infrastructure. You can get the following types of external repositories:

* Amazon S3 object storage.
* Microsoft Azure object storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the ID of an external repository that you want to get. | String | True | Named | False |
| Name | Specifies the name of an external repository that you want to get. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRExternalRepository object that contains settings of external repositories added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting External Repository by Name

|  |  |
| --- | --- |
| This command allows you to get an external repository named External Repository.  |  | | --- | | Get-VBRExternalRepository -Name "External Repository" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting External Repository by ID

|  |  |
| --- | --- |
| This command allows you to get an external repository by the external repository ID.  |  | | --- | | Get-VBRExternalRepository -Id "0x0x0xxx-000x-0x0x-000-000x00000x0x" | |


