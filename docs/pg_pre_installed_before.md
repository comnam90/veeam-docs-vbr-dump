---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pg_pre_installed_before.html"
last_updated: "2/5/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before creating a protection group, consider the following prerequisites and limitations:

* A protection group for pre-installed Veeam Agents offers a limited set of deployment and management operations. To learn more, see [Working with Protection Groups for Pre-Installed Veeam Agents](protection_group_tasks.md#flex) and [Managing Protected Computers Added to Protection Group for Pre-Installed Veeam Agents](agents_protected_computers_manage.md#pre_installed).

* You can add a protection group of the computers with pre-installed backup agents type only to a Veeam Agent backup job managed by Veeam Agent. Veeam Agent backup jobs managed by the backup server are not supported by this type of protection groups. To learn more about backup job types, see [Working with Veeam Agent Backup Jobs and Policies](backup_job_tasks.md).
* You cannot add a computer from a protection group for pre-installed Veeam Agents to any other protection group.

|  |
| --- |
| TIP |
| After you create the protection group, you will be able to move a Veeam Agent for Microsoft Windows or Veeam Agent for Linux computer to another protection group. To learn more, see [Moving Computer to Protection Group](agents_protected_computers_move.md). |

* Do not install Veeam Agent on servers that are used as components of the Veeam Backup & Replication infrastructure. This includes Veeam backup servers, backup repositories, proxy servers, mount servers, distribution servers, gateway and helper appliance servers, and any other backup infrastructure component that has the Veeam Mount Service deployed.

* If you want to add new computers to a protection group for pre-installed Veeam Agents after updating the TLS certificate on the Veeam backup server, you must first recreate the setup files. To learn more, see [Specify Packages](protection_group_packages.md).


