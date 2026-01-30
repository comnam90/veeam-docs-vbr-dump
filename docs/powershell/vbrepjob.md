---
title: "VBREPJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrepjob.html"
last_updated: "2/7/2025"
product_version: "13.0.1.1071"
---

# VBREPJob


Contains a backup job created by Veeam Agent operating in the standalone mode.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| RepositoryId | GUID | ID of backup repository used to store backups. |
| ObjectsCount | int | Number of objects in the job. |
| IsEnabled | bool | Indicates if the job is enabled (TRUE) or disabled (FALSE). |
| NextRun | DateTime? | Date and time of the next job run. |
| Target | Object | Target repository name. |
| Type | [VBRJobType](vbrjob.md) | Job type: Endpoint. |
| LastResult | [VBRSessionResult](enums.md#vbrsessionresult) | Session result. |
| LastState | [VBRSessionState](enums.md#vbrsessionstate) | Session state. |
| Id | GUID | Job ID. |
| Name | string | Job name. |
| Description | string | Job description. |

Related Commands

[Veeam Agent Standalone Mode](endpoint.md)


