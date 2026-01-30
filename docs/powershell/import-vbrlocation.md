---
title: "Import-VBRLocation"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/import-vbrlocation.html"
last_updated: "2/20/2024"
product_version: "13.0.1.1071"
---

# Import-VBRLocation


Short Description

Imports geographic locations to Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Import-VBRLocation -Path <string>  [<CommonParameters>] |

Detailed Description

This cmdlet imports geographic locations to Veeam Backup & Replication from an XML file.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies the name of the XML file. The cmdlet will import locations to Veeam Backup & Replication from this file. | String | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Importing Geographic Locations from XML File

This command imports geographic locations to Veeam Backup & Replication from an XML file.

|  |
| --- |
| Import-VBRLocation -Path "C:\Locations\BackupNorth.xml" |


