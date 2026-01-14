---
title: "Add-VBRCloudProviderCredentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcloudprovidercredentials.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Add-VBRCloudProviderCredentials

In this article

Short Description

Adds cloud provider credentials records to Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRCloudProviderCredentials -Name <string> -Password <string> [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds cloud provider credentials records to Veeam Backup & Replication.

|  |
| --- |
| ![Add-VBRCloudProviderCredentials](images/icon_note.webp) Note: |
| This cmdlet requires a PSCredential object. Use the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet to create the PSCredentials object. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the login for cloud provider credentials records. | String | True | Named | False |
| Password | Specifies the password for cloud provider credentials records. | String | True | Named | False |
| Description | Specifies the description for cloud provider credentials records. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRCloudProviderCredentials

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Cloud Provider Credentials

|  |  |
| --- | --- |
| This command adds cloud provider credentials records to the Veeam Backup & Replication infrastructure.  |  | | --- | | Add-VBRCloudProviderCredentials -Name "Cloud Login" -Password "Cloud password" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Cloud Provider Credentials with Secure String Option

|  |  |
| --- | --- |
| This example shows how to add cloud provider credentials records with the secure string option to the Veeam Backup & Replication infrastructure.  |  | | --- | | $securepassword = Read-Host -Prompt "Enter password" -AsSecureString  Add-VBRCloudProviderCredentials -Name "Cloud Login" -Password $securepassword |  Perform the following steps:   1. Run the [Read-Host](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.3&viewFallbackFrom=powershell-6) cmdlet. Specify the Prompt parameter value. Provide the AsSecureString parameter. Save the result to the $securepassword variable. 2. Run the Add-VBRCloudProviderCredentials cmdlet. Specify the Name parameter value. Set the $securepassword variable as the Password parameter value. |

Page updated 3/4/2024

Page content applies to build 13.0.1.1071
