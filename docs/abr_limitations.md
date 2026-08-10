---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/abr_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


Application backup repositories have the following limitations:

* 1 application backup repository consumes 1 Veeam Universal License on Veeam Data Platform Foundation plan or above. Socket-based licensing is not supported.

|  |
| --- |
| Note |
| Once the application backup repository license is revoked, the snapshot schedule is automatically disabled. |

* You must allocate a dedicated application backup repository for each application. Do not configure multiple applications to write backup data to the same application backup repository. Although this configuration is technically possible, it prevents granular recovery of individual applications after a snapshot revert operation.

* The application backup repository cannot be hosted on remote Fibre Channel or iSCSI devices. For more information, see [Deploying Application Backup Repository](deploy_abr.md).
* Manual changes of the snapshots are not supported, as it may result in an unpredictable system behavior and data loss.

* Due to the application-agnostic nature of the snapshot recovery procedure, data quiescence and consistency cannot be guaranteed. The post-revert operations are your responsibility; no official support will be provided for specific customer scenarios.

Requirements and Limitations for Access Permissions

* The following NFS versions are supported for the NFS share access configuration:

* If the access permissions are configured by host or IP mask, NFS version 3 and NFS version 4 are supported.
* If Kerberos authentication is enabled, NFS version 4 is required.
* If Kerberos authentication is enabled and you use Microsoft Windows-based NFS clients, only NFS version 3 is supported due to the OS version limitations.

* For Kerberos authentication, the application backup repository host must be added to the domain.
* When the NFS share is accessed by host/IP address permission without Kerberos authentication, Veeam Backup & Replication uses a service user veeam-usr-abr-nfs for all read/write actions on the share. When the share is access using Kerberos authentication, the user identity is kept.
* [For Microsoft Windows-based NFS clients] To avoid issues with the authentication of the appliance service user, you must add the following DWORD (32-bit) values in decimal base to HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\ClientForNFS\CurrentVersion\Default registry path:

|  |
| --- |
| AnonymousGid = 399  AnonymousUid = 399 |

* The restrictions imposed by the access permissions based on IP addresses and based on Kerberos authentication protocol are combined. For example, if there is at least one IP address added to the access permission list, and a user specified in the Kerberos authentication list tries to connect from a non-allowed IP address, the user will be denied access. However, if no IP addresses are specified in the access permission list, users with Kerberos permissions can access the NFS share from any IP address. In this case, All hosts are allowed will be listed in the access permission list.
* If you enable Kerberos authentication for access permissions, the NFS share is mounted using one of following Kerberos protocols: krb5p, krb5i, krb5.
* If one server has multiple application backup repositories hosted on it, the data of each application backup repository is isolated and you need to grant access permissions for each application backup repository separately.

Page updated 2026-07-29

