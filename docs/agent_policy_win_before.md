---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_policy_win_before.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a Veeam Agent backup policy in the Veeam Backup & Replication console, check the following prerequisites:

* The Veeam Backup & Replication license must have a sufficient number of instances to process servers and workstations that you plan to add to the Veeam Agent backup policy. To learn more, see [Licensing Requirements](agents_licensing_requirements.md).

* The target location where you plan to store backup files must have enough free space.
* Protection groups that you want to add to the policy must be configured in advance.
* [For backup policies targeted at the cloud repository] The Veeam Cloud Connect service provider must be added in the Veeam backup console.

Veeam Agent backup policies have the following limitations:

* Veeam Agent for Microsoft Windows does not back up data to which symbolic links are targeted. It only backs up the path information that the symbolic links contain. After restore, identical symbolic links are created in the restore destination.

* You cannot map a Veeam Agent backup policy to a Veeam Agent backup chain created by another type of a Veeam Agent backup job. After you change the mode of a Veeam Agent computer, Veeam Backup & Replication starts a new backup chain in a target location specified in the backup policy settings.

* Veeam Agent does not support creating transaction log backups in a cloud repository. You cannot enable transaction log backup options in the properties of the backup policy targeted at a cloud repository.

* You cannot add a Veeam Agent computer protected by a backup job managed by the backup server to a Veeam Agent backup policy. To add such a computer to a Veeam Agent backup policy, first remove the computer from the backup job managed by the backup server.

Page updated 1/13/2026

Page content applies to build 13.0.1.1071
