---
title: "VBRAzureApplianceSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrazureappliancesession.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRAzureApplianceSession

In this article

Contains Linux VM restore appliance deploy session.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| Log | [VBRLogItem](vbrlogitem.md) | Session log. |
| Id | GUID | Session ID. |
| State | [VBRSessionState](enums.md#vbrsessionstate) | Session state. |
| Result | [VBRSessionResult](enums.md#vbrsessionresult) | Session result. |
| JobId | GUID | Job ID. |
| CreationTime | DateTime? | Date and time of session creation. |
| EndTime | DateTime? | Date and time of session end. |

Related Commands

[Deploy-VBRAzureLinuxRestoreAppliance](deploy-vbrazurelinuxrestoreappliance.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
