---
title: "Network"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_system_requirements_network.html"
last_updated: "4/13/2026"
product_version: "13.0.1.2067"
---

# Network


Consider the following network requirements:

* Veeam Agent must be able to establish a direct IP connection to the Veeam Backup & Replication server. If a direct IP connection is not available — for example, when Veeam Backup & Replication is located behind the NAT gateway and Veeam Agent is not — Veeam Agent cannot communicate with Veeam Backup & Replication.
* For initial communication between Veeam backup server and Veeam Agent computers running on Microsoft Windows, one of the following authentication protocols is used:

* Kerberos

Kerberos is required for communication between Veeam Agent for Microsoft Windows and a Linux-based Veeam backup server. Linux-based Veeam backup servers do not support NTLM. For more information about this protocol, see [Kerberos Authentication](kerberos_authentication.md).

* Windows New Technology LAN Manager (NTLM)

Windows-based Veeam backup servers support this legacy protocol for compatibility.

|  |
| --- |
| NOTE |
| Neither Kerberos nor NTLM is required if you plan to install Veeam Agent using Veeam Deployment Kit. For more information, see [Deploying Veeam Agent Using Veeam Deployment Kit](agents_deploy_deployer.md). |

* Domain names of all managed servers added to the Veeam backup infrastructure and computers you want to back up must be resolvable into IPv4 or IPv6 addresses.

Keep in mind that for Veeam Agent computers that are included in a protection group for pre-installed Veeam Agents, only Veeam Backup & Replication server must be resolvable into IPv4 or IPv6 address.

* [For SSH connection to Linux- and Unix-based computers] Veeam Backup & Replication expects only standard command responses; unexpected additional console output may cause SSH connection failure. We recommend that you disable all login banners, MOTDs (Message of the Day) and remove output-generating code from shell initialization files for the account that Veeam Backup & Replication uses to connect to the host.


