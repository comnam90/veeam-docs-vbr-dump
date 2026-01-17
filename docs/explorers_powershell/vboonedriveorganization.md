---
title: "VBOOneDriveOrganization"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vboonedriveorganization.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VBOOneDriveOrganization


Contains details about a Microsoft OneDrive organization.

| Property | Type | Description |
| --- | --- | --- |
| Name | String | Microsoft OneDrive organization, in the following format:  <organization\_name> (<backup\_job\_name>) (<date\_and\_time\_when\_restore\_session\_was\_created>)  For example:  qwbs.onmicrosoft.com (Backup job) (2/27/2025 10:41:17 AM)  Note that the backup job name is only displayed if you have specified the job name when starting the restore session. |

Related Commands

[Get-VEODOrganization](get-veodorganization.md)


