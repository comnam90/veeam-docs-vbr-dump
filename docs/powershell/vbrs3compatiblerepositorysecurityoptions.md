---
title: "VBRS3CompatibleRepositorySecurityOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrs3compatiblerepositorysecurityoptions.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# VBRS3CompatibleRepositorySecurityOptions

In this article

Contains settings that Veeam Agent uses to access S3 compatible repositories

Properties

| Property | Type | Description |
| --- | --- | --- |
| RepositoryId | Guid | Repository ID |
| AccessControlPolicy | [VBRS3CompatibleAccessControlPolicyType](enums.md#VBRS3CompatibleAccessControlPolicyType) | Access control type. |
| IAMEndpoint | String | IP address |
| STSEndpoint | String | Security token |

Related Commands

* [Get-VBRS3CompatibleRepositorySecurityOptions](get-vbrs3compatiblerepositorysecurityoptions.md)
* [Set-VBRS3CompatibleRepositorySecurityOptions](set-vbrs3compatiblerepositorysecurityoptions.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
