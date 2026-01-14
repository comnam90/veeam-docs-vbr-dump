---
title: "Remove-VBRCloudProviderCredentials"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcloudprovidercredentials.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCloudProviderCredentials

In this article

Short Description

Removes cloud provider credentials records from Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRCloudProviderCredentials -Credentials <VBRCloudProviderCredentials> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes cloud provider credentials records from Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credentials | Specifies cloud provider credentials records that you want to remove. | Accepts the VBRCloudProviderCredentials object. To get this object, run the [Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md) cmdlet. | True | 0 | True (ByValue) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Cloud Provider Credentials Records

This example shows how to remove cloud provider credentials records.

|  |
| --- |
| $creds = Get-VBRCloudProviderCredentials -Name "Cloud credentials"  Remove-VBRCloudProviderCredentials -Credentials $creds -Confirm |

Perform the following steps:

1. Run the [Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable.
2. Run the Remove-VBRCloudProviderCredentials cmdlet. Set the $creds variable as the Credentials parameter value. Provide the Confirm parameter.

Related Commands

[Get-VBRCloudProviderCredentials](get-vbrcloudprovidercredentials.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
