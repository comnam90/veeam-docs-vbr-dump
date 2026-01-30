---
title: "Generate-VBRLicenseUsageReport"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/generate-vbrlicenseusagereport.html"
last_updated: "8/5/2024"
product_version: "13.0.1.1071"
---

# Generate-VBRLicenseUsageReport


Short Description

Creates reports on license usage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Generate-VBRLicenseUsageReport -Path <string> -Type <VBRLicenseUsageReportType> {Html | Pdf | Json}  [<CommonParameters>] |

Detailed Description

This cmdlet creates a report on license usage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies a name of file and the path to the folder. The cmdlet will save a report with the specified name to this folder. | String | True | Named | False |
| Type | Specifies a type of the report file. You can generate a report in one of the following file types:   * Html * Pdf * Json | [VBRLicenseUsageReportType](enums.md#VBRLicenseUsageReportType) | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLicenseUsageReport object that contains license usage report.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating HTML Report

|  |  |
| --- | --- |
| This command creates the HTML report on license usage. The report is saved as the report.html file to the C:\Users\Administrator\VeeamReports\ folder.  |  | | --- | | Generate-VBRLicenseUsageReport -Path "C:\Users\Administrator\VeeamReports\NovemberReport" -Type Html | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating PDF Report

|  |  |
| --- | --- |
| This command creates the PDF report on license usage. The report is saved as the report.pdf file to the C:\Users\Administrator\VeeamReports\ folder.  |  | | --- | | Generate-VBRLicenseUsageReport -Path "C:\Users\Administrator\VeeamReports\JanuaryReport" -Type Pdf | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating JSON Report

|  |  |
| --- | --- |
| This command creates the JSON report on license usage. The report is saved as the report.json file to the C:\Users\Administrator\VeeamReports\ folder.  |  | | --- | | Generate-VBRLicenseUsageReport -Path "C:\Users\Administrator\VeeamReports\DecemberReport" -Type Json | |


