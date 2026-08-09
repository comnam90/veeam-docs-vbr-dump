---
title: "Deploying Veeam Agent Using Veeam Deployment Kit"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_deploy_deployer.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Deploying Veeam Agent Using Veeam Deployment Kit


If you create a [protection group for individual computers](protection_group_individual.md) or a [protection group with Microsoft Active Directory objects](protection_group_ad.md), you have an option to install Veeam Agent on Microsoft Windows, Linux and IBM AIX computers using certificate-based authentication instead of credentials. To do so, you must download Veeam Deployment Kit on the computer you want to protect, install the required packages and then add the computer to the protection group.

Deployment scenario depends on the Veeam Agent you work with:

* [Veeam Agent for Microsoft Windows](agents_deployer_vaw.md)
* [Veeam Agent for Linux](agents_deployer_val.md)
* [Veeam Agent for IBM AIX](agents_deployer_vau.md)

|  |
| --- |
| IMPORTANT |
| Consider the following:   * Deploying Veeam Agent for Oracle Solaris using Veeam Deployment Kit is not supported. * Failover clusters are not supported when you use Veeam Deployment Kit to install Veeam Agent on computers in a protection group with Microsoft Active Directory objects. |

Page updated 2026-07-02

