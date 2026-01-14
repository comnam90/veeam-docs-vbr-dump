---
title: "Set-VBRCloudProviderCredentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudprovidercredentials.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudProviderCredentials

In this article

Short Description

Modifies cloud provider credential records.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCloudProviderCredentials -Credentials <VBRCloudProviderCredentials> [-Name <string>] [-Password <string>] [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies cloud provider credentials records are added to Veeam Backup & Replication.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credentials | Specifies cloud provider credentials records that you want to modify. | Accepts the VBRCloudProviderCredentials object. To get this object, run the [Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies the login for the cloud provider credentials records. | String | False | Named | False |
| Password | Specifies the password for the cloud provider credentials records. | String | False | Named | False |
| Description | Specifies the description for the cloud provider credentials records. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRCloudProviderCredentials

Examples

Modifying Login for Cloud Provider Credentials Records

This example shows how to modify a login for cloud provider credentials records.

|  |
| --- |
| $creds = Get-VBRCloudProviderCredentials -Name "Cloud credentials"  Set-VBRCloudProviderCredentials -Credentials $creds -Name "New Login" |

Perform the following steps:

1. Run the [Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable.
2. Run the Set-VBRCloudProviderCredentials cmdlet. Set the $creds variable as the Credentials parameter value. Specify the Name parameter value.

Related Commands

[Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
