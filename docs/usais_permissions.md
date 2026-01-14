---
title: "Universal Storage API Integrated Systems Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/usais_permissions.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# Universal Storage API Integrated Systems Permissions

In this article

|  |
| --- |
| Note |
| For most storage systems, the account must be assigned the Administrator role. If other permissions can be used, they are listed below. |

The account used to connect to a Universal Storage API integrated system must be assigned a necessary role in the storage system console and have a set of necessary permissions.

* For DataCore, the account must have the following permissions:

+ General
+ Port
+ Host
+ Virtual disk
+ Snapshot
+ Physical disk

* For Dell PowerMax, the account must be assigned the Storage Administrator role.

* For Dell PowerStore, the account must be assigned one of the following roles:

+ Administrator
+ Storage Administrator
+ Storage Operator

* For Fujitsu ETERNUS AF and DX series, the account must be assigned the Software role.

* For Hitachi VSP/VSP One Block, the account must be assigned the following roles:

+ Storage Administrator (View Only)
+ Storage Administrator (Provisioning)
+ Storage Administrator (Local Copy)

* For NEC Storage M Series, the account must be assigned the Administrator role.

* For NetApp SolidFire/HCI, the account must have the following permissions:

+ Volumes
+ Cluster Admins

* For Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile), the account must be assigned the Veeam Admin Role.

Page updated 10/17/2025

Page content applies to build 13.0.1.1071
