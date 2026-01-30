---
title: "VBRADContainer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbradcontainer.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRADContainer


Contains a scope of Active Directory objects.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Domain | [VBRADDomain](vbraddomain.md) | The Active Directory domain connection object. |
| Entity | [VBRADEntity[]](vbradentity.md) | The array of Active Directory objects added to the protection scope. |
| ExcludeVMs | bool | Indicates if all VMs are excluded from the protection scope. |
| ExcludeOfflineComputers | bool | Indicates if computers that have been offline for over 30 days are excluded from the protection scope. |
| ExcludeComputers | bool | Indicates if specific Active Directory objects are excluded from the protection scope. |
| ExcludeEntity | [VBRADEntity[]](vbradentity.md) | The array of Active Directory objects that are excluded from the protection scope. |
| MasterCredentials | CCredentials | Master account credentials for authenticating with all Active Directory objects in a protection scope. |
| UseCustomCredentials | bool | Indicates if custom credentials are used for authenticating with some Active Directory objects. |
| CustomCredentials | VBRADEntityCredentials[] | Credentials for authenticating with associated Active Directory objects. |

Related Commands

[New-VBRADContainer](new-vbradcontainer.md)


