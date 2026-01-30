---
title: "VBRBestPracticeInfo"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrbestpracticeinfo.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# VBRBestPracticeInfo


Contains the results of Security and Compliance Analyzer checks.

Properties

| Property | Type | Description |
| --- | --- | --- |
| ID | GUID | The session ID. |
| Type | [VBRBestPracticeType](enums.md#VBRBestPracticeType) | The Security and Compliance Analyzer check. |
| Status | [VBRBestPracticeStatus](enums.md#VBRBestPracticeStatus) | The status of a Security and Compliance Analyzer check. |
| Note | String | Notes about a check. |

Related Commands

* [Start-VBRSecurityComplianceAnalyzer](start-vbrsecuritycomplianceanalyzer.md)
* [Get-VBRSecurityComplianceAnalyzerResults](get-vbrsecuritycomplianceanalyzerresults.md)


