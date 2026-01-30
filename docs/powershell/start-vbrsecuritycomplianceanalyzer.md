---
title: "Start-VBRSecurityComplianceAnalyzer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrsecuritycomplianceanalyzer.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# Start-VBRSecurityComplianceAnalyzer


Short Description

Starts the Security & Compliance Analyzer scan.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRSecurityComplianceAnalyzer [-Wait] [<CommonParameters>] |

Detailed Description

This cmdlet starts the Security & Compliance Analyzer scan. You can access the results of the scan in the System node of the History view.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRSecurityComplianceAnalyzerSession

Examples

Starting Security & Compliance Analyzer Scan

This command starts the Security & Compliance Analyzer scan.

|  |
| --- |
| Start-VBRSecurityComplianceAnalyzer |

Related Commands

[Get-VBRSecurityComplianceAnalyzerResults](get-vbrsecuritycomplianceanalyzerresults.md)


