---
title: "VBRADForestDomainRestoreSpec"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbradforestdomainrestorespec.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRADForestDomainRestoreSpec


Contains a domain controller in a Microsoft Active Directory forest.

Properties

Properties

| Property | Type | Description |
| DomainControllerFqdn | String | Fully qualified domain name (FQDN) of the domain controller. |
| OibId | GUID | ID of the domain controller in the Veeam Backup & Replication configuration database. |
| CredentialsId | GUID | Credentials ID. |
| AdSchemaVersion | Int32 | Microsoft Active Directory schema version. |

Related Commands

* [New-VBRViADForestDomainRestoreSpec](new-vbrviadforestdomainrestorespec.md)
* [New-VBRHvADForestDomainRestoreSpec](new-vbrhvadforestdomainrestorespec.md)

Page updated 2026-06-07

