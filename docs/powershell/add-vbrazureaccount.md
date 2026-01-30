---
title: "Add-VBRAzureAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrazureaccount.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Add-VBRAzureAccount


Short Description

Adds a Microsoft Azure compute account to Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add the Microsoft Azure compute account.

|  |
| --- |
| Add-VBRAzureAccount -Name <string> [-Region {Global | China | Government}] [-AzureCredentials <CCredentials>] [-Description <string>] [-TenantId <string>] [-ApplicationId <string>] [-SecretKey <string>] [-CertificatePath <string>] [-Password <string>]  [<CommonParameters>] |

* Add Microsoft Azure Stack Hub account.

|  |
| --- |
| Add-VBRAzureAccount -ResourceManagerEndpoint <string> -Name <string> [-AzureCredentials <CCredentials>] [-Description <string>] [-TenantId <string>] [-ApplicationId <string>] [-SecretKey <string>] [-CertificatePath <string>] [-Password <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a credentials record for Microsoft Azure compute account to Veeam Backup & Replication and imports information about subscriptions and resources associated with the Microsoft Azure compute account.

You can add the following types of the accounts:

* Microsoft Azure account
* Microsoft Azure Stack Hub compute account

The cmdlet will open a Microsoft Azure wizard. Follow the steps of the wizard to add the account.

|  |
| --- |
| Important |
| Consider the following:   * This cmdlet does not create a Microsoft Azure compute account. You must set up the Microsoft Azure account beforehand.  * This cmdlet does not support Microsoft Azure compute accounts with the Azure Service Manager (ASM, also known as a "classic" type). |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of credentials record for for Microsoft Azure compute account. The cmdlet will add credentials record with this name. | String | True | Named | False |
| ResourceManagerEndpoint | To connect to Microsoft Azure Stack Hub compute account.  Specifies the virtual IP address of Azure Resource Manager. The account will connect to this resource manager.  Note: You must specify the IP address in the following format: management.<region>.<FQDN>. | String | True | Named | False |
| Region | Specifies the region type of the Microsoft Azure account. You can select the following types of regions:   * Global * China * Government | VBRAzureRegionType | False | Named | False |
| Description | Specifies a description of credentials record for Microsoft Azure compute account. The cmdlet will add credentials record with this description. | String | False | Named | False |
| AzureCredentials | Note: This parameter is obsolete and will be deprecated in next version.  Specifies an exiting Azure AD application. Veeam Backup & Replication will use this Azure AD application to connect to Microsoft Azure. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| TenantId | For existing account connection type.  Specifies an ID of a tenant (directory) where the AD application resides. The cmdlet will use this tenant ID to connect to the Azure AD application. | String | False | Named | False |
| ApplicationId | Specifies the ID of the AD application. The cmdlet will use this application to connect to Microsoft Azure. | String | False | Named | False |
| SecretKey | For the password-based authentication.  Specifies the application secret that the cmdlet will use to authenticate against Microsoft Azure. | String | False | Named | False |
| CertificatePath | For certificate-based authentication.  Specifies a path to the folder where the certificate is located. The cmdlet will use it to authenticate against Azure. | String | False | Named | False |
| Password | For certificate-based authentication.  Specifies a password that the cmdlet will use it to authenticate against Azure. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureAccount](vbrazureaccount.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Microsoft Azure Compute Account

|  |  |
| --- | --- |
| This command adds the Microsoft Azure compute account into your Veeam Backup & Replication infrastructure with the following settings:   * The name of the account is Azure Compute Administrator. * The ID of a tenant (directory) where the AD application resides is XXXXXXXX. * The ID of the application is 42f83f98. * The application secret is XXXXXXXXXXXXXXXXXXX. * The region type is Global.   |  | | --- | | Add-VBRAzureAccount -Name "Azure Compute Administrator" -TenantId "XXXXXXXX" -ApplicationId "42f83f98" -SecretKey "XXXXXXXXXXXXXXXXXXX" -Region Global | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Microsoft Azure Stack Hub Compute Account

|  |  |
| --- | --- |
| This command adds the Microsoft Azure Stack Hub compute account named Azure Stack Administrator. The account connects to the management.local.veeamstack.external virtual IP address of Azure Resource Manager.  |  | | --- | | Add-VBRAzureAccount -ResourceManagerEndpoint "management.local.azurestack.external" -Name "Azure Stack Administrator" | |


