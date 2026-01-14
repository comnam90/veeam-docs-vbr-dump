---
title: "Set-VBRVCenterName"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvcentername.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBRVCenterName

In this article

Short Description

Modifies VMware vCenter name.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRVCenterName -OldVCenterName <String>  [<CommonParameters>] |

Detailed Description

This cmdlet modifies VMware vCenter name by adding the old postfix to its original name.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| OldVCenterName | Specifies an old VMware vCenter name you want to modify. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Modifying VMware vCenter Name

This example shows how to modify the name of vcenter70 VMware vCenter.

|  |
| --- |
| Set-VBRVCenterName -OldVCenterName "vcenter70" |

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
