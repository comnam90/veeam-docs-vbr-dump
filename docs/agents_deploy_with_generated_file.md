---
title: "Deploying Veeam Agents"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_deploy_with_generated_file.html"
last_updated: "12/2/2025"
product_version: "13.0.1.1071"
---

# Deploying Veeam Agents

In this article

To install Veeam Agent on a computer using Veeam Backup & Replication, you can add the computer to a protection group from the Veeam Backup & Replication console. After the computer is added to a protection group, Veeam Backup & Replication can automatically deploy Veeam Agent to the computer using administrative credentials during the rescan operation, or you can install Veeam Agent later if the automatic Veeam Agent deployment option is not enabled in the protection group settings. To learn more, see [Rescan Job](agents_discovery_job.md).

For Microsoft Windows and Linux computers, you have an option to pre-install Veeam Installer Service and Veeam Deployer Service on a computer that you plan to add to a protection group. In this case, Veeam Backup & Replication will be able to communicate with the computer using a certificate instead of credentials. To learn more, see [Deploying Veeam Agent Using Veeam Deployment Kit](agents_deploy_deployer.md).

For environments where remote deployment is not possible, you can generate setup files and a configuration file from Veeam Backup & Replication, manually install Veeam Agent on the target computer, and then apply the configuration file. This approach is required for computers that you want to add to a protection groups for pre-installed Veeam Agents. To learn more, see [Deploying Veeam Agents Using Generated Setup Files](agents_deploy_package.md).

Related Topics

* [Protection Group Types](agents_protection_groups_types.md)
* [Creating Protection Groups](protection_group_add.md)

Page updated 12/2/2025

Page content applies to build 13.0.1.1071
