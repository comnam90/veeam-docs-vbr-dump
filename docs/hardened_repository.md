---
title: "Hardened Repository"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository.html"
last_updated: "11/27/2025"
product_version: "13.0.1.1071"
---

# Hardened Repository

In this article

To protect your backup files from loss as a result of malware activity or unplanned actions, you can add a hardened repository based on a Linux server to your backup infrastructure.

A hardened repository supports the following features:

* Immutability: when you add a hardened repository, you specify the time period while backup files must be immutable. During this period, backup files stored in this repository cannot be moved, modified or deleted, but can be copied.
* Secure Authentication: when you add a hardened repository, you specify the method used to authenticate connections.

* Certificate-based: No user name or password is required; authentication is performed using certificates. It is recommended for environments where Kerberos is disabled or unavailable, or for enhanced security. This option is available for hardened repositories deployed from the Veeam Infrastructure Appliance.
* Single-use credentials: Credentials that are used only once to deploy [Veeam Data Mover](veeam_transport_service.md), while adding the Linux server to the backup infrastructure. These credentials are not stored in the backup infrastructure. Even if the Veeam Backup & Replication server is compromised, the attacker cannot get the credentials and connect to the hardened repository.

To interact with the hardened repository, Veeam Backup & Replication uses SHA256RSA self-signed certificates with 2048-bit RSA key.

|  |
| --- |
| Note |
| For security reasons, you cannot assign other roles to the hardened repository except for the VMware backup proxy working in the Network mode. For more information, see [Hardened Repository as VMware Backup Proxy](hardened_repository_vmware_backup_proxy.md). |

In This Section

* [About Hardened Repository](hardened_repository_about.md)
* [Requirements and Limitations](hardened_repository_limitations.md)
* [Using Veeam Infrastructure Appliance as Hardened Repository](hardened_repository_appliance_prepare.md)
* [Using Backup Server as Hardened Repository](hardened_repository_backup_server.md)
* [Adding Hardened Repositories](hardened_repository_add.md)
* [Managing Hardened Repository](hardened_repository_managing.md)

Page updated 11/27/2025

Page content applies to build 13.0.1.1071
