---
title: "New-VBRIrisInstancePathMappingRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbririsinstancepathmappingrule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRIrisInstancePathMappingRule


Short Description

Defines path mapping rules for InterSystems IRIS instance restore.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRIrisInstancePathMappingRule -OriginalPath <String> -TargetPath <String>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRIrisInstancePathMappingRule](vbririsinstancepathmappingrule.md) object that maps an original path of an InterSystems IRIS instance to a target path.

Use this object as the PathMapping parameter value when you run the [Start-VBRIrisInstanceRestore](start-vbririsinstancerestore.md) cmdlet to restore an InterSystems IRIS instance to a different location. To get the original paths of a restore point, run the [Get-VBRIrisInstanceOriginalPath](get-vbririsinstanceoriginalpath.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| OriginalPath | Specifies the original path of the InterSystems IRIS instance data. To get original paths of a restore point, run the [Get-VBRIrisInstanceOriginalPath](get-vbririsinstanceoriginalpath.md) cmdlet. | String | True | Named | False |
| TargetPath | Specifies the target path to which you want to restore the InterSystems IRIS instance data. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRIrisInstancePathMappingRule](vbririsinstancepathmappingrule.md) object that contains a path mapping rule.

Examples

Creating a Path Mapping Rule for InterSystems IRIS Instance Restore

This example shows how to create a path mapping rule that redirects InterSystems IRIS instance data to a new target path.

|  |
| --- |
| $rule = New-VBRIrisInstancePathMappingRule -OriginalPath "/usr/irissys/mgr" -TargetPath "/mnt/restore/mgr" |

Run the New-VBRIrisInstancePathMappingRule cmdlet. Specify the OriginalPath and TargetPath parameter values. Save the result to the $rule variable to use with other cmdlets.

Related Commands

* [Get-VBRIrisInstanceOriginalPath](get-vbririsinstanceoriginalpath.md)

Page updated 2026-06-18

