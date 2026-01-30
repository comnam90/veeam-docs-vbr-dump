---
title: "VBRSocketLicenseSummary"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrsocketlicensesummary.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRSocketLicenseSummary


Contains details on the per-socket license usage.

Properties

| Property | Type | Description |
| --- | --- | --- |
| LicensedSocketsNumber | int | Total number of CPU sockets on protected hosts. |
| UsedSocketsNumber | int | Number of CPU sockets that have already been used. |
| RemainingSocketsNumber | int | Number of CPU sockets that remain available. |
| Workload | [VBRLicensedSocketWorkload](vbrlicensedsocketworkload.md)[] | Name of the licensed host. |

Related Commands

[Get-VBRSocketLicenseSummary](get-vbrsocketlicensesummary.md)


