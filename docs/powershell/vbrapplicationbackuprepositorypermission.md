---
title: "VBRApplicationBackupRepositoryPermission"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationbackuprepositorypermission.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRApplicationBackupRepositoryPermission


Contains permission settings for a host to access the NFS share of an application backup repository.

VBRApplicationBackupRepositoryPermission

| Property | Type | Description |
| Mode | VBRPermissionMode | Specifies the permissions granted to the host. Accepted values:   * Read — grants read-only access. * ReadWrite — grants read and write access. |
| ServerName | String | Specifies the DNS name or IP mask of the host. |

Related Commands

[New-VBRApplicationBackupRepositoryPermission](new-vbrapplicationbackuprepositorypermission.md)

Page updated 2026-05-28

