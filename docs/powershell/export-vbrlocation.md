---
title: "Export-VBRLocation"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/export-vbrlocation.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Export-VBRLocation

In this article

Short Description

Exports geographic locations from Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Export-VBRLocation -Path <string> [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet exports geographic locations created in Veeam Backup & Replication to an XML file.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies the path to the XML file. The cmdlet will export locations to this file. | String | True | Named | True (ByValue, ByProperty Name) |
| Force | Defines that the cmdlet will overwrite the existing destination XML file without asking a user. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Exporting Geographic Locations to XML File

This command exports geographic locations from Veeam Backup & Replication to an XML file.

|  |
| --- |
| Export-VBRLocation -Path "C:\Locations\BackupNorth.xml" |

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
