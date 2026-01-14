---
title: "VBRInstanceLicenseSummary"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrinstancelicensesummary.html"
last_updated: "12/9/2024"
product_version: "13.0.1.1071"
---

# VBRInstanceLicenseSummary

In this article

Contains details on the per-instance license usage.

Properties

| Property | Type | Description |
| --- | --- | --- |
| LicensedInstancesNumber | int | Total number of instances that are available in the license scope. |
| UsedInstancesNumber | int | Number of instances that have already been used. |
| NewInstancesNumber | int | Number of new instances. |
| RentalInstancesNumber | int | Number of rental instances. |
| Object | [VBRInstanceLicenseSummaryObject](vbrinstancelicensesummaryobject.md)[] | Details on protected workloads. |
| Workload | [VBRLicensedInstanceWorkload](vbrlicensedinstanceworkload.md)[] | Protected workloads. |

Related Commands

[Get-VBRInstanceLicenseSummary](get-vbrinstancelicensesummary.md)

Page updated 12/9/2024

Page content applies to build 13.0.1.1071
