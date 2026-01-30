---
title: "VBRAzureADAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrazureadaccount.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRAzureADAccount


Contains settings of Azure Entra ID storage account.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Region | [VBRAzureBlobRegionType](enums.md#VBRAzureBlobRegionType) | Microsoft Azure region. |
| StorageAccountName | String | Azure Entra ID storage account. |
| TenantId | String | Tenant ID. |
| ApplicationId | String | Microsoft Azure subscription type. |
| Name | string | Account name. |
| Id | GUID | Account ID. |
| ResourceManagerEndpoint | String | Azure Stack resource management endpoint. |

Related Commands

* [Add-VBRAzureADAccount](add-vbrazureadaccount.md)
* [Get-VBRAzureADAccount](get-vbrazureadaccount.md)
* [Set-VBRAzureADAccount](set-vbrazureadaccount.md)
* [Remove-VBRAzureADAccount](remove-vbrazureadaccount.md)


