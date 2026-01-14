---
title: "Prerequisites"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/linux_server_before_begin.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Prerequisites

In this article

Before you add a Linux server to the Veeam Backup & Replication infrastructure, check the [required permissions](required_permissions.md#rphost) and the following prerequisites.

Linux Firewalls

When you add a Linux server to the backup infrastructure, Veeam Backup & Replication automatically opens ports used by the [Veeam Data Mover](veeam_transport_service.md) on the Linux server. Generally, Veeam Backup & Replication automatically open ports for most of popular firewalls (iptables, ufw, firewall-cmd). However, if for some reason the ports are not opened, you can open the ports manually. You can also specify these ports at the [SSH Connection](linux_server_ssh.md) step of the New Linux Server wizard. Note that ports are opened dynamically: if 10 concurrent jobs are running, Veeam Backup & Replication opens ports 2500-2509.

If you use the firewalld tool, you can configure firewall rules to open ports only in necessary zones. By default, Veeam Backup & Replication opens ports in all active firewalld zones. If your firewall is configured for different zones, and you want to minimize security holes, you can configure Veeam Backup & Replication to open the ports only for certain zones. To do this, perform the following:

1. On the helper host or target Linux host, create the /etc/VeeamNetConfig file and define the following parameter:

|  |
| --- |
| FirewalldZones=zone\_name\_1, zone\_name\_2 |

where zone\_name\_1, zone\_name\_2 is a list of zone names where the ports must be open. Veeam Backup & Replication will skip the zones that are not in this list.

1. [Only for helper host] If you select a Linux host that is already added to the Veeam Backup & Replication infrastructure, you should also add required zones to the /opt/veeam/transport/VeeamTransportConfig file.

|  |
| --- |
| FirewalldZones=zone\_name\_1, zone\_name\_2 |

|  |
| --- |
| Note |
| Veeam Backup & Replication opens the port 2500 in all zones even if you have specified the required zones in configuration files. |

TLS Connection

Linux servers use the TLS connection. You can disable the TLS connection for the servers that do not support the TLS connection in the configuration file on the Linux-based backup server or with registry values on the Microsoft Windows-based backup server. For more information, contact Veeam Customer Support.

Page updated 10/20/2025

Page content applies to build 13.0.1.1071
