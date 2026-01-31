---
title: "Network"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_system_requirements_network.html"
last_updated: "1/30/2026"
product_version: "13.0.1.1071"
---

# Network


Consider the following about network requirements:

* Veeam Agent must be able to establish a direct IP connection to the Veeam Backup & Replication server. If a direct IP connection is not available — for example, when Veeam Backup & Replication is located behind the NAT gateway and Veeam Agent is not — Veeam Agent cannot communicate with Veeam Backup & Replication.
* For communication between Veeam backup infrastructure and computers you want to back up, one of the following authentication protocols is required:

* [Not applicable to Veeam Agent for Mac and Veeam Agent for Unix] Kerberos

To learn more, see [Kerberos Authentication](kerberos_authentication.md).

* [Not applicable to Veeam Backup & Replication on Linux] Windows New Technology LAN Manager (NTLM)

* Kerberos authentication is required for communication between Veeam backup infrastructure and Veeam Agent for Microsoft Windows computers you want to back up. To learn more, see [Kerberos Authentication](kerberos_authentication.md).
* Domain names of all managed servers added to the Veeam backup infrastructure and computers you want to back up must be resolvable into IPv4 or IPv6 addresses.

Keep in mind that for Veeam Agent computers that are included in a protection group for pre-installed Veeam Agents, only Veeam Backup & Replication server must be resolvable into IPv4 or IPv6 address.

* [For SSH connection to Linux- and Unix-based computers] Veeam Backup & Replication expects only standard command responses; unexpected additional console output may cause SSH connection failure. We recommend that you disable all login banners, MOTDs (Message of the Day) and remove output-generating code from shell initialization files for the account that Veeam Backup & Replication uses to connect to the host.


