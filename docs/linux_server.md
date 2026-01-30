---
title: "Linux Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/linux_server.html"
last_updated: "9/5/2025"
product_version: "13.0.1.1071"
---

# Linux Server


You can add a Linux server with local, directly attached storage or mounted NFS as a backup repository. The storage can be a local disk, directly attached disk-based storage (such as a USB hard drive), NFS share, or iSCSI/FC SAN LUN in case the server is connected into the SAN fabric.

A Linux repository with single-use credentials and the immutability feature provides additional protection for your backup files. For more information, see [Hardened Repository](hardened_repository.md).

Linux Backup Repository Deployment

To communicate with a Linux-based repository, Veeam Backup & Replication uses two [Veeam Data Movers](veeam_transport_service.md) that are responsible for data processing and transfer:

* Veeam Data Mover on the backup proxy
* Veeam Data Mover on the Linux-based backup repository

For more information about Veeam Data Movers communication with a Linux-based server, see [Veeam Data Mover](veeam_transport_service.md).

Veeam Data Mover establishes a connection with the source-side Data Mover on the backup proxy, enabling efficient data transfer over LAN or WAN.

![Linux Server](images/repository_linux.webp)

vPower NFS Server

Linux repositories can be configured to function as vPower NFS Servers. In this case, Veeam Backup & Replication will run the Veeam vPower NFS Service directly in the backup repository (namely, on the managing Linux server to which storage is attached) and provide ESXi hosts with transparent access to backed-up VM images stored on the backup repository. For more information, see [Veeam vPower NFS Service](vpower_nfs_service.md).

Requirements for Linux Backup Repositories

A machine performing the role of a repository must meet the following requirements:

* The role of the repository can be assigned to a Linux machine (physical or virtual). The machine must meet the system requirements. For more information, see [System Requirements](system_requirements.md#repo).

* You must add the machine to the Veeam Backup & Replication console as a managed server.
* If you want to use Fast Clone in the Linux-based backup repository, the machine must also meet requirements listed in section [Fast Clone](backup_repository_block_cloning.md#linux).
* Depending on the Linux distribution, Veeam services use one of the following Linux firewall managers to operate correctly:

+ firewalld
+ ufw
+ iptables
+ [For IPv6] ip6tables

If none of these firewall managers are installed, make sure that you open all required ports manually. For more information, see [Ports](used_ports.md).

You can place both repositories (hardened and standard) on one Linux server only if you used single-use credentials when adding the host. Standard repository is a repository added with persistent credentials and disabled immutability. For more hardened repository limitations, see [Requirements and Limitations](hardened_repository_limitations.md).

Related Topics

* [Adding Linux Repositories Using Console](linux_repository_add.md)
* [Adding Linux Repositories Using Web UI](linux_repository_add_web.md)


