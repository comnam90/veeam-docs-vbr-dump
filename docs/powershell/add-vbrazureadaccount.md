---
title: "Add-VBRAzureADAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrazureadaccount.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Add-VBRAzureADAccount

In this article

Short Description

Adds Azure Entra ID-based storage accounts to Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add Azure Entra ID-based storage accounts using a password-based authentication (application secret).

|  |
| --- |
| Add-VBRAzureADAccount -ApplicationId <String> -CertificatePath <String> -StorageAccountName <String> -TenantId <String> [-Description <String>] [-Password <String>] [-Region {Global | China | Government}]  [<CommonParameters>] |

* Add Azure Entra ID-based storage accounts using a certificate.

|  |
| --- |
| Add-VBRAzureADAccount -ApplicationId <String> [-Description <String>] [-Region {Global | China | Government}] -SecretKey <String> -StorageAccountName <String> -TenantId <String>  [<CommonParameters>] |

Detailed Description

This cmdlet adds Azure Entra ID-based storage accounts to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ApplicationId | Specifies the ID of Microsoft Entra ID application. | String | True | Named | False |
| CertificatePath | For certificate-based authentication.  Specifies a path to the folder where the certificate is located. The cmdlet will use it to authenticate against Microsoft Entra. | String | True | Named | False |
| StorageAccountName | Specifies a name of an Azure Entra ID-based storage account. The cmdlet will use it as a friendly name and will add the storage account using this name. | String | True | Named | False |
| TenantId | For existing account connection type.  Specifies an ID of a tenant (directory) where the Microsoft Entra ID application resides. | String | True | Named | False |
| SecretKey | For password-based authentication.  Specifies an application secret that the cmdlet will use to authenticate against Microsoft Entra. | String | True | Named | False |
| Description | Specifies a description of an Azure Entra ID-based storage account. The cmdlet will add this storage account with this description. | String | False | Named | False |
| Password | For password-based authentication.  Specifies a password that the cmdlet will use it to authenticate against Microsoft Entra. | String | False | Named | False |
| Region | Specifies the Microsoft Azure region where Azure Entra ID-based storage account is located. You can select the following types of regions:   * Global * Government * China | [VBRAzureBlobRegionType](enums.md#VBRAzureBlobRegionType) | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureADAccount](vbrazureadaccount.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Azure Entra ID-Based Storage Account with Password-Based Authentication

|  |  |
| --- | --- |
| This command adds the Azure Entra ID-based storage account to Veeam Backup & Replication. The cmdlet uses a password-based authentication.  |  | | --- | | Add-VBRAzureADAccount -ApplicationId "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" -CertificatePath "C:\Users\Administrator\Locked" -StorageAccountName "EntraID" -TenantId "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" -Description "Administrator Entra ID"  -Password "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" -Region Global | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Azure Entra ID-Based Storage Account Using Certificate

|  |  |
| --- | --- |
| This command adds the Azure Entra ID-based storage account to Veeam Backup & Replication. The cmdlet uses a certificate-based authentication.  |  | | --- | | Add-VBRAzureADAccount -ApplicationId "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" -Description "Administrator Entra ID" -Region Global -SecretKey XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX -StorageAccountName "EntraID" -TenantId "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" | |

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
