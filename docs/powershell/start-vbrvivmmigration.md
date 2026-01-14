---
title: "Start-VBRViVMMigration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvivmmigration.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Start-VBRViVMMigration

In this article

Short Description

Starts the MORef IDs update.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRViVMMigration -File <String>  [<CommonParameters>] |

Detailed Description

This cmdlet starts the MORef IDs update.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| File | Specifies a path to the migration task file. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting MORef IDs Update

This example shows how to start the MORef IDs update.

|  |
| --- |
| Start-VBRViVMMigration -File C:\Folder\vcenter70\_old\_to\_vcenter70\_migration\_task |

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
