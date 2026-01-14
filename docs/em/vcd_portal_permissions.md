---
title: "vcd_portal_permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vcd_portal_permissions.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---


In this article

Members of VMware Cloud Director organizations can use Veeam Self-Service Backup Portal to back up and restore resources of their organizations.

The following organization members have access to Veeam Self-Service Backup Portal:

* Cloud Director organization administrator
* Cloud Director organization member that has all of the following rights granted in VMware Cloud Director:

* General: Administrator Control
* General: Administrator View
* User: View Users and Groups
* Organization: View Organization Administrative Details (required for access using Veeam Plug-in for VMware Cloud Director only)

* Any Cloud Director organization members whose roles (or associated LDAP user roles) are defined in registry keys and with the Group / User: View right granted in VMware Cloud Director. For more information, contact [Veeam Customer Support](https://www.veeam.com/support.html).

For details on how to access the portal, see [Accessing Veeam Self-Service Backup Portal](vcd_portal_access.md).

|  |
| --- |
| Note |
| Cloud Director system administrators cannot access Veeam Self-Service Backup Portal since they are not organization members. |

Page updated 6/18/2024

Page content applies to build 13.0.1.1071
