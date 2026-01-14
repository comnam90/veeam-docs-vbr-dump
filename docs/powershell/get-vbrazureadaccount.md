---
title: "Get-VBRAzureADAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureadaccount.html"
last_updated: "11/13/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureADAccount

In this article

Short Description

Returns Azure Entra ID-based storage accounts.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Azure Entra ID-based storage accounts by their IDs.

|  |
| --- |
| Get-VBRAzureADAccount -Id <Guid[]>  [<CommonParameters>] |

* Get Azure Entra ID-based storage accounts by their friendly names.

|  |
| --- |
| Get-VBRAzureADAccount [-Name <String[]>]  [<CommonParameters>] |

* Get Azure Entra ID-based storage accounts by their names.

|  |
| --- |
| Get-VBRAzureADAccount [-StorageAccountName <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Azure Entra ID-based storage accounts added to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for Azure Entra ID-based storage accounts. The cmdlet will return storage accounts with these ID. | Guid[] | True | Named | False |
| Name | Specifies an array of friendly names for storage accounts. The cmdlet will return storage accounts with these names.  Note: The friendly names match the names of the storage accounts. | String[] | False | Named | False |
| StorageAccountName | Specifies an array of names for Azure Entra ID storage account. The cmdlet will return Microsoft Entra ID user accounts with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureADAccount](vbrazureadaccount.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Azure Entra ID-Based Storage Accounts by ID

|  |  |
| --- | --- |
| This command returns Azure Entra ID-based storage accounts with the following IDs: cfe6a67f-f322-446d-92e3-cf1da7cbf192 and 1242a067-8292-406b-8035-8b0aefb187bf.  |  | | --- | | Get-VBRAzureADAccount -Id Guid "cfe6a67f-f322-446d-92e3-cf1da7cbf192", "1242a067-8292-406b-8035-8b0aefb187bf" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Azure Entra ID-Based Storage Accounts by Names

|  |  |
| --- | --- |
| This command returns Azure Entra ID-based storage accounts with the Azure Entra ID Admin name.  |  | | --- | | Get-VBRAzureADAccount -Name "Azure Entra ID Admin" | |

Page updated 11/13/2024

Page content applies to build 13.0.1.1071
