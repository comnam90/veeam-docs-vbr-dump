---
title: "Generate-VBRViMigrationSpecificationFile"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/generate-vbrvimigrationspecificationfile.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Generate-VBRViMigrationSpecificationFile

In this article

Short Description

Generates a migration task file.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Generate-VBRViMigrationSpecificationFile -ExportPath <String> -NewVCenterName <String> -OldVCenterName <String>  [<CommonParameters>] |

Detailed Description

This cmdlet generates a migration task file which contains the list of MORef ID changes.

After the task file is generated, verify that the proposed MORef ID changes are valid before continuing the MORef ID update process.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ExportPath | Specifies a path where the task file will be generated. | String | True | Named | False |
| NewVCenterName | Specifies a new VMware vCenter name. | String | True | Named | False |
| OldVCenterName | Specifies an old VMware vCenter name. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Generating Migration Task File

This example shows how generate the migration task file for the old VMware vCenter named vcenter70\_old and the new VMware vCenter named vcenter70.

|  |
| --- |
| Generate-VBRViMigrationSpecificationFile -ExportPath C:\Folder -NewVCenterName vcenter70 -OldVCenterName vcenter70\_old |

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
