---
title: "Veeam Agent Web UI Features"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_management_interfaces.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Veeam Agent Web UI Features


In the Veeam Backup & Replication web UI, you can perform the following agent management tasks:

* [Create and manage protection groups.](#protection_groups)
* [Create and manage Veeam Agent backup jobs and policies.](#backup_jobs)
* [Perform restore and recovery operations.](#restore)

For the full list of operations that are available in the Veeam Backup & Replication web UI, see [Veeam Backup & Replication Web UI](vbr_web_console.md).

Working with Protection Groups

In the Veeam Backup & Replication web UI, you can perform the following operations for these protection group types:

* Create and manage protection groups that include [individual computers](agents_protection_groups_types.md#individual) and [Active Directory objects](agents_protection_groups_types.md#ad).
* Manage computers from the [Untrusted](agents_protection_groups_default.md#untrusted), [Offline](agents_protection_groups_default.md#offline) and [Out of Date](agents_protection_groups_default.md#ood) predefined protection groups.
* View computers that belong to protection groups for [computers listed in a CSV file](agents_protection_groups_types.md#csv), [cloud machines](agents_protection_groups_types.md#cloud), [computers with pre-installed backup agents](agents_protection_groups_types.md#flexible), and the [Manually Added](agents_protection_groups_default.md#manual) predefined protection group.
* Filter the list of computers from the displayed protection groups by operating system, agent installation status, last seen and last backup time.

|  |
| --- |
| NOTE |
| The [Unmanaged](agents_protection_groups_default.md#unmanaged) predefined protection group is not visible in the Veeam Backup & Replication web UI. |

Working with Veeam Agent Backup Jobs and Policies

In the Veeam Backup & Replication web UI, you can perform most operations with [backup jobs](agents_job.md) and [backup policies](agents_policy.md) for Veeam Agent for Microsoft Windows and Veeam Agent for Linux computers.

You can also perform the following operations on backups: view backup [permissions](agent_backup_permissions.md), [grant or revoke computer access to backups](agents_protected_computers_access.md), and [delete backups from disk](agent_backup_delete.md).

Veeam Agent for Mac and Veeam Agent for Unix backup jobs and policies are not supported. Existing Veeam Agent for Mac backups are also not visible in the Veeam Backup & Replication web UI.

|  |
| --- |
| NOTE |
| The following operations are not available in the Veeam Backup & Replication web UI:   * Using [Veeam Cloud Connect repositories](agents_cloud_connect.md) as the target for backup jobs. * The [Move To](agents_protected_computers_move.md) and [Quick Backup](agents_quick_backup_start.md) operations. * Viewing history and aggregated statistics for backup policies. |

Performing Restore and Recovery Operations

In the Veeam Backup & Replication web UI, you can perform the following restore and recovery operations:

* Perform [file-level recovery](guest_file_recovery.md) from Windows and Linux backups.
* [Publish disks](publishing_disks.md) from agent backups.
* Perform [Instant Recovery](instant_recovery.md) to VMware vSphere and Microsoft Hyper-V.
* Perform [remote bare metal recovery](integration_instant_restore_media_remote.md) of Veeam Agent for Microsoft Windows computers.
* Create [recovery tokens](agent_backup_recovery_token.md).
* Create [Veeam Recovery Media](recovery_media_create_web.md).

|  |
| --- |
| NOTE |
| The [Allow virtual recovery partition creation](agents_protection_group_advanced_vaw_web.md) option can be enabled in both the Veeam Backup & Replication console and the Veeam Backup & Replication web UI. However, the remote bare metal recovery wizard is available in the Veeam Backup & Replication web UI only. |

Page updated 2026-07-23

