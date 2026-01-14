---
title: "VBRAzureAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrazureaccount.html"
last_updated: "10/19/2023"
product_version: "13.0.1.1071"
---

# VBRAzureAccount

In this article

Contains Microsoft Azure account.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Description | string | Microsoft Azure description. |
| LinuxRestoreEnabled | bool | Indicates if the account allows restore of Linux-based machines (if the account has Linux helper appliances) (TRUE) or not (FALSE). |
| Region | [VBRAzureRegionType](enums.md#VBRAzureRegionType) | Microsoft Azure region. |
| AzureCredentials | CCredentials | Microsoft Azure credentials. |
| Type | [VBRAzureModelType](enums.md#VBRAzureModelType) | Microsoft Azure subscription type. |
| Name | string | Account name. |
| Id | GUID | Account ID. |
| ResourceManagerEndpoint | String | Azure Stack resource management endpoint. |

Related Commands

* [Add-VBRAzureAccount](add-vbrazureaccount.md)
* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Set-VBRAzureAccount](set-vbrazureaccount.md)
* [Remove-VBRAzureAccount](remove-vbrazureaccount.md)

Page updated 10/19/2023

Page content applies to build 13.0.1.1071
