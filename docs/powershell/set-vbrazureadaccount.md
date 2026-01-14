---
title: "Set-VBRAzureADAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazureadaccount.html"
last_updated: "11/13/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAzureADAccount

In this article

Short Description

Modifies settings of Azure Entra ID-based storage accounts.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modifies settings of  Azure Entra ID-based storage accounts added with password-based authentication.

|  |
| --- |
| Set-VBRAzureADAccount -Account <VBRAzureADAccount> [-ApplicationId <String>] [-CertificatePath <String>] [-Description <String>] [-Password <String>] [-StorageAccountName <String>] [-TenantId <String>]  [<CommonParameters>] |

* Modifies settings of  Azure Entra ID-based storage accounts added with a certificate.

|  |
| --- |
| Set-VBRAzureADAccount -Account <VBRAzureADAccount> [-ApplicationId <String>] [-Description <String>] [-SecretKey <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Azure Entra ID-based storage accounts.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies the Azure Entra ID-based storage account which settings you want to modify. | Accepts the VBRAzureADAccount object. To create this object, run the [Get-VBRAzureADAccount](get-vbrazureadaccount.md) cmdlet. | True | Named | True |
| ApplicationId | Specifies the ID of Microsoft Entra ID application. | String | False | Named | False |
| CertificatePath | For certificate-based authentication.  Specifies a path to the folder where the certificate is located. The cmdlet will use it to authenticate against Microsoft Entra. | String | False | Named | False |
| Description | Specifies a description of an Azure Entra ID-based storage account. The cmdlet will modify this description. | String | False | Named | False |
| Password | For certificate-based authentication.  Specifies a password that the cmdlet will use it to authenticate against Microsoft Entra. | String | False | Named | False |
| StorageAccountName | Specifies a name of an Azure Entra ID-based storage account. The cmdlet will modify this name. | String | False | Named | False |
| TenantId | For existing account connection type.  Specifies an ID of a tenant (directory) where the Microsoft Entra ID application resides. | String | False | Named | False |
| SecretKey | For password-based authentication.  Specifies an application secret that the cmdlet will use to authenticate against Microsoft Entra. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureADAccount](vbrazureadaccount.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Microsoft Entra ID Application for Azure Entra ID-Based Storage Accounts

|  |  |
| --- | --- |
| This example shows how to modify the ID of Microsoft Entra ID application of  the Azure Entra ID-based storage account.  |  | | --- | | $account = Get-VBRAzureADAccount -Name "EntraID"  Set-VBRAzureADAccount -Account $account -ApplicationId "YYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYY" |  Perform the following steps:   1. Run the [Get-VBRAzureADAccount](get-vbrazureadaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the Set-VBRAzureADAccount cmdlet. Set the $account variable as the Account parameter value. Specify the ApplicationId parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Application Secret for Azure Entra ID-Based Storage Accounts

|  |  |
| --- | --- |
| This example shows how to modify application secret settings of the Azure Entra ID-based storage account.  |  | | --- | | $account = Get-VBRAzureADAccount -Name "EntraID"  Set-VBRAzureADAccount -Account $account -SecretKey "YYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYY" |  Perform the following steps:   1. Run the [Get-VBRAzureADAccount](get-vbrazureadaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the Set-VBRAzureADAccount cmdlet. Set the $account variable as the Account parameter value. Specify the SecretKey parameter value. |

Related Commands

[Get-VBRAzureADAccount](get-vbrazureadaccount.md)

Page updated 11/13/2024

Page content applies to build 13.0.1.1071
