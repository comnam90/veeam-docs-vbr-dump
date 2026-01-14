---
title: "Get-VBRSecurityComplianceAnalyzerResults"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsecuritycomplianceanalyzerresults.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# Get-VBRSecurityComplianceAnalyzerResults

In this article

Short Description

Returns Security & Compliance Analyzer scan results.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSecurityComplianceAnalyzerResults [-Session <VBRSecurityComplianceAnalyzerSession>] [<CommonParameters>] |

Detailed Description

This cmdlet returns the results of a Security & Compliance Analyzer scan.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the ID of the scan session you want to view.  Session IDs can be found in Security and Compliance Analyzer logs. They are stored in the directory var/log/VeeamBackup on the backup server. | VBRSecurityComplianceAnalyzerSession | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Security & Compliance Analyzer Results From Last Session

|  |  |
| --- | --- |
| This command returns the results of the most recent Security & Compliance Analyzer scan.  |  | | --- | | Get-VBRSecurityComplianceAnalyzerResults | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Security & Compliance Analyzer Results From Specific Session

|  |  |
| --- | --- |
| This command returns the results of the Security & Compliance Analyzer scan with the session ID 1695.  |  | | --- | | Get-VBRSecurityComplianceAnalyzerResults -Session "1695" | |

Related Commands

[Start-VBRSecurityComplianceAnalyzer](start-vbrsecuritycomplianceanalyzer.md)

Page updated 8/4/2025

Page content applies to build 13.0.1.1071
