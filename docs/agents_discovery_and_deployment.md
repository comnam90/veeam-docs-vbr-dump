---
title: "Protected Computers Discovery and Veeam Agent Deployment"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_discovery_and_deployment.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# Protected Computers Discovery and Veeam Agent Deployment

In this article

Veeam Backup & Replication supports automated and manual deployment of Veeam Agents on computers in your infrastructure:

* [Automated and manual deployment using the Veeam backup console](#from_console)

* [Manual deployment using external tools](#using_external_tools)

Automated and Manual Deployment Using Veeam Backup Console

You can deploy Veeam Agent for Microsoft Windows, Veeam Agent for Linux, Veeam Agent for Oracle Solaris and Veeam Agent for IBM AIX from the Veeam Backup & Replication console. To learn more about supported scenarios, see [Supported Veeam Agents](agents_supported_veeam_agents.md).

To deploy Veeam Agents, Veeam Backup & Replication needs to discover computers whose data you want to back up. To enable discovery, you organize your computers into one or more protection groups. Protection group settings define what Veeam Agent computers Veeam Backup & Replication will discover and how the discovery process will run. To learn more, see [Protection Groups](agents_protection_groups.md).

You can also disable automated Veeam Agent installation when [configuring a protection group](agents_protection_group_options.md). In this case, you will need to use the Veeam Backup & Replication console to install Veeam Agent on every computer included in the protection group. To learn more, see [Installing Veeam Agent](agents_protected_computers_install.md).

Manual Deployment Using External Tools

You can manually deploy all supported Veeam Agents using external tools. To learn more about supported scenarios, see [Supported Veeam Agents](agents_supported_veeam_agents.md).

To deploy Veeam Agents using external tools, you need to perform the following operations:

1. Create a protection group for pre-installed Veeam Agents using Veeam Backup & Replication. To learn more about this type of protection groups, see [Protection Group Types](agents_protection_groups_types.md#flexible).

After a new protection group is created, Veeam Backup & Replication generates a set of setup files required for the Veeam Agent deployment. This set of setup files includes an XML configuration file with a TLS certificate. This certificate is used to secure the first communication between Veeam Backup & Replication and Veeam Agents. It helps Veeam Agents identify themselves and make sure that computers connecting to the Veeam backup server are really the ones that they claim to be.

To learn how to check information about the currently used certificate, see [Configuring Security Settings](agents_manage_tls_and_ssh.md).

|  |
| --- |
| IMPORTANT |
| Veeam Backup & Replication generates the same TLS certificate for the first communication between Veeam Backup & Replication and all computers you want to include in protection groups for pre-installed Veeam Agents. So, it is strongly recommended that you securely store and share Veeam Agent setup files. Otherwise, any computer that has this certificate can connect to the Veeam backup server. |

1. Using external tools, transfer Veeam Agent setup files to the computer you want to protect. Then, deploy Veeam Agent and connect it to Veeam backup server with an XML configuration file. To learn more, see [Deploying Veeam Agents Using Generated Setup Files](agents_deploy_package.md).

Once you connect Veeam Agent to the Veeam backup server, Veeam Backup & Replication discoveries the computer and replaces the TLS certificate for all Veeam Agent computers with another TLS certificate that is unique for each computer. After that, you can find the connected computer in the Veeam Backup & Replication console displayed as a member of the protection group.

In This Section

* [Protection Groups](agents_protection_groups.md)
* [Rescan Job](agents_discovery_job.md)

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
