---
title: "Get-VBRAzureAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureaccount.html"
last_updated: "7/18/2025"
product_version: "13.0.1.1071"
---

# Get-VBRAzureAccount

In this article

Short Description

Returns Microsoft Azure accounts added to Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Microsoft Azure accounts by name and model.

|  |
| --- |
| Get-VBRAzureAccount [-Name <string[]>] [<CommonParameters>] |

* Get Microsoft Azure accounts by ID.

|  |
| --- |
| Get-VBRAzureAccount [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Microsoft Azure accounts added to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of names of the accounts. The cmdlet will return the accounts that match these names. | String[] | False | Named | False |
| Id | Specifies the array of IDs of the accounts. The cmdlet will return the accounts that match these IDs. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureAccount](vbrazureaccount.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Microsoft Azure Accounts

|  |  |
| --- | --- |
| This command returns all Microsoft Azure accounts added to Veeam Backup & Replication.  |  | | --- | | Get-VBRAzureAccount | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Microsoft Azure Account by Name

|  |  |
| --- | --- |
| This command returns the Microsoft Azure account named RestoreToAzure@Veeam.com added to Veeam Backup & Replication.  |  | | --- | | Get-VBRAzureAccount -Name RestoreToAzure@Veeam.com | |

Page updated 7/18/2025

Page content applies to build 13.0.1.1071
