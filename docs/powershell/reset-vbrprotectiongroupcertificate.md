---
title: "Reset-VBRProtectionGroupCertificate"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/reset-vbrprotectiongroupcertificate.html"
last_updated: "5/2/2024"
product_version: "13.0.1.1071"
---

# Reset-VBRProtectionGroupCertificate

In this article

Short Description

Removes a certificate associated with a protection group with a flexible scope.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Reset-VBRProtectionGroupCertificate -ProtectionGroup <VBRProtectionGroup[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a certificate associated with a protection group with a flexible scope.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ProtectionGroup | Specifies an array of protection groups for which you want to remove certificates. | Accepts the VBRProtectionGroup[] object. To create this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True(ByValue, ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Certificate Associated with Specific Protection Groups

This example shows how to remove a certificate associated with the LinuxPG, macOSPG protection groups with a flexible scope.

|  |
| --- |
| $protectiongroup = Get-VBRProtectionGroup -Name "LinuxPG, macOSPG"  Reset-VBRProtectionGroupCertificate -ProtectionGroup $protectiongroup |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $protectiongroup variable.
2. Run the Reset-VBRProtectionGroupCertificate cmdlet. Set the $protectiongroup variable as the ProtectionGroup parameter value.

Related Commands

[Get-VBRProtectionGroup](get-vbrprotectiongroup.md)

Page updated 5/2/2024

Page content applies to build 13.0.1.1071
