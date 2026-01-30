---
title: "Find-VBRTapeCatalogVersion (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrtapecatalogversion.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Find-VBRTapeCatalogVersion (obsolete)


Short Description

Looks for versions of files stored on tapes.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works but may not be supported in further versions. |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Find-VBRTapeCatalogVersion [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>]  -OR-  Find-VBRTapeCatalogVersion [-CatalogFile <CatalogueFile>] [-Name <String[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet looks for versions of files stored on tapes that are managed by Veeam Backup & Replication.

File version is used as a file restore point.

You can get the list of all files and their versions that are stored on tapes or narrow down the output by file name or object of file you need.

Run the [Find-VBRTapeCatalog](find-vbrtapecatalog.md) cmdlet to get the list of files stored on tapes.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name of the file you want to get versions for, or search conditions.  You can specify multiple names separated by commas. | String[] | False | Named | False |
| CatalogFile | Specifies the file you want to get versions for. | Accepts the CatalogueFile object. To get this object, run the [Find-VBRTapeCatalog](find-vbrtapecatalog.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Most Recent Version of File

|  |  |
| --- | --- |
| This example shows how to look for the most recent version of the Payroll\_Marketing.html file.  |  | | --- | | Find-VBRTapeCatalog -Name "Payroll\_Marketing.html" | Find-VBRTapeCatalogVersion | Select -First 1 |  Perform the following steps:   1. Run the [Find-VBRTapeCatalog](find-vbrtapecatalog.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Find-VBRTapeCatalogVersion cmdlet. 3. Pipe the cmdlet output to the Select cmdlet. Specify the First parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Versions of Specific File

|  |  |
| --- | --- |
| This example shows how to look for versions of the Payroll\_Marketing.html file.  |  | | --- | | $file = Find-VBRTapeCatalog -Name "Payroll\_Marketing.html"  $file | Find-VBRTapeCatalogueVersion |  Perform the following steps:   1. Run the [Find-VBRTapeCatalog](find-vbrtapecatalog.md) cmdlet. Specify the Name parameter value. Save the result to the $file variable. 2. Pipe the cmdlet output to the Find-VBRTapeCatalogVersion cmdlet. |

Related Commands

[Find-VBRTapeCatalog](find-vbrtapecatalog.md)


