---
title: "Set-VBRAzureAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazureaccount.html"
last_updated: "7/18/2025"
product_version: "13.0.1.1071"
---

# Set-VBRAzureAccount

In this article

Short Description

Modifies Microsoft Azure compute account added to Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAzureAccount -Account <VBRAzureAccount> [-ApplicationId <String>] [-AzureCredentials <CCredentials>] [-CertificatePath <String>] [-Description <String>] [-Name <String>] [-Password <String>] [-SecretKey <String>] [-TenantId <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an existing Microsoft Azure compute account added to the Veeam Backup & Replication managing console. The cmdlet opens a Microsoft Azure wizard. Follow the steps of the wizard to enter the new settings.

|  |
| --- |
| Important |
| This cmdlet does not support Microsoft Azure compute account with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies the Azure account that you wand to edit. | Accepts the [VBRAzureAccount](vbrazureaccount.md) object. To get this object, run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| ApplicationId | Specifies the ID of the AD application. The cmdlet will use this application to connect to Microsoft Azure. | String | False | Named | False |
| AzureCredentials | Note: This parameter is obsolete and will be deprecated in next version.  Specifies an exiting Azure AD application. Veeam Backup & Replication will use this Azure AD application to connect to Microsoft Azure. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| CertificatePath | For certificate-based authentication.  Specifies a path to the folder where the certificate is located. The cmdlet will use it to authenticate against Microsoft Azure. | String | False | Named | False |
| Name | Specifies a name of credentials record for for Microsoft Azure compute account. The cmdlet will add credentials record with this name. | String | False | Named | False |
| Description | Specifies a description of credentials record for for Microsoft Azure compute account. The cmdlet will apply this description to credentials record. | String | False | Named | False |
| TenantId | For existing account connection type.  Specifies an ID of a tenant (directory) where the AD application resides. The cmdlet will use this tenant ID to connect to the Azure AD application. | String | False | Named | False |
| ApplicationId | Specifies the ID of the AD application. The cmdlet will use this application to connect to Microsoft Azure. | String | False | Named | False |
| SecretKey | For the password-based authentication.  Specifies the application secret that the cmdlet will use to authenticate against Microsoft Azure. | String | False | Named | False |
| CertificatePath | For certificate-based authentication.  Specifies a path to the folder where the certificate is located. The cmdlet will use it to authenticate against Microsoft Azure. | String | False | Named | False |
| Password | For certificate-based authentication.  Specifies a password that the cmdlet will use it to authenticate against Microsoft Azure. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureAccount](vbrazureaccount.md)

Examples

Editing ID of AD Application of Microsoft Azure Compute Account

This example shows how to edit the ID of the AD application for an existing Microsoft Azure compute account.

|  |
| --- |
| $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  Set-VBRAzureAccount -Account $account -ApplicationId "42f83f64" |

Perform the following steps:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) to get the account. Specify the Name parameter value. Save the result to the $account variable.
2. Run the Set-VBRAzureAccount cmdlet. Set the $account variable as the Account parameter value. Specify the ApplicationId parameter value.

Related Commands

[Get-VBRAzureAccount](get-vbrazureaccount.md)

Page updated 7/18/2025

Page content applies to build 13.0.1.1071
