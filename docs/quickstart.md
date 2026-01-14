---
title: "Getting Started"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/quickstart.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# Getting Started

In this article

To start using the Veeam Plug-In management functionality in Veeam Backup & Replication, you must perform the following operations:

1. Deploy Veeam Backup & Replication.

For details, see [Deployment](deployment.md).

1. Configure security settings.

By default, Veeam Backup & Replication offers the following settings to establish a secure connection between the backup server and protected computers:

* To establish a secure connection between parties, Veeam Backup & Replication uses the default self-signed certificate.
* Veeam Backup & Replication allows all new Linux hosts to establish a connection to the backup server.

You can use the default security settings or change them if needed. To learn more, see [Configuring Security Settings](security_settings.md).

1. Add computers with databases that you want to protect to the Veeam Backup & Replication inventory.

In Veeam Backup & Replication, computers with databases that you want to protect are organized into protection groups. You can use the Veeam Backup & Replication console to create one or more protection groups that include individual computers, Microsoft Active Directory objects, or list of computers imported from a CSV file. To learn more, see [Creating Protection Groups](protection_group_create.md).

1. Discover computers and deploy Veeam Plug-Ins.

During protection group configuration, you can set Veeam Backup & Replication to automatically discover computers and install Veeam Plug-Ins on discovered computers. In this case, these operations are performed immediately after you create a protection group. To learn more, see [Discovery and Deployment Options](protection_group_options.md).

You can also run discovery and deployment operations manually for an individual computer in a protection group. To learn more, see [Rescanning Protected Computer](protected_computers_rescan.md)..

1. Configure an application backup policy.

You can configure one or more application backup policies and add to these policies one or more protection groups, Active Directory objects and individual computers. In Veeam Backup & Replication, you can configure application backup policies for the following Veeam Plug-Ins:

* [Veeam Plug-In for Oracle RMAN](create_policy_create_oracle_rman.md)
* [Veeam Plug-In for SAP HANA](create_policy_create_sap_hana.md)
* [Veeam Plug-In for SAP on Oracle](create_policy_create_sap_oracle.md)
* [Veeam Plug-In for Microsoft SQL Server](create_policy_create_microsoft_sql_server.md)

1. Manage application backup policies.

You can start, stop, enable and disable application backup policies to administer data protection operations on protected computers. To learn more, see [Managing Application Backup Policies](manage_policy.md).

|  |
| --- |
| Tip |
| After the first successful run of an application backup policy, you can also run the backup job from the computer with Veeam Plug-In. For details, see [Starting Backup Job on Veeam Plug-In Side](manage_policy_start_job_from_vp.md). |

1. In case of a disaster, you can use created application backups to restore database data.

To learn more, see [Managing Application Backups](application_backups.md).

Page updated 11/7/2025

Page content applies to build 13.0.1.1071
