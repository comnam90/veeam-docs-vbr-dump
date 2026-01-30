---
title: "Overview"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_introduction.html"
last_updated: "12/4/2025"
product_version: "13.0.1.1071"
---

# Overview


Veeam Backup & Replication lets you deploy and manage the following Veeam Agents on computers in your infrastructure:

* Veeam Agent for Microsoft Windows
* Veeam Agent for Linux
* Veeam Agent for IBM AIX
* Veeam Agent for Oracle Solaris
* Veeam Agent for Mac

|  |
| --- |
| NOTE |
| In Veeam documentation, Veeam Agent for IBM AIX and Veeam Agent for Oracle Solaris are collectively referred to as Veeam Agent for Unix. IBM AIX and Oracle Solaris servers are collectively referred to as Unix servers or Unix machines. |

You do not need to install, set up and operate Veeam Agent on every computer whose data you want to protect. Instead, you can perform the whole set of deployment, administration, data protection and disaster recovery tasks on Veeam Agent computers remotely from the Veeam Backup & Replication console.

Veeam Backup & Replication offers the following Veeam Agent management capabilities:

* Automated deployment and management of Veeam Agents. You can set up Veeam Backup & Replication to automatically discover computers that you want to protect with Veeam Agent for Microsoft Windows and Veeam Agent for Linux and Unix machines that you want to protect with Veeam Agent for Oracle Solaris and Veeam Agent for IBM AIX. You can also manually deploy all supported Veeam Agents on computers you want to protect. Once Veeam Agent is deployed on protected computers, you can use the Veeam Backup & Replication console to manage Veeam Agents on multiple computers.
* Centralized configuration and management of Veeam Agent backup jobs on protected computers. You can use the Veeam Backup & Replication console to create and manage Veeam Agent backup jobs on computers in your infrastructure whose data you want to protect.
* Centralized management of backups created by Veeam Agent backup jobs. If you choose to create Veeam Agent backups on a backup repository managed by the Veeam backup server, you can use the Veeam Backup & Replication console to restore data from these backups.

In This Section

* [Veeam Agent Management Infrastructure](agents_infrastructure.md)
* [Protected Computers Discovery and Veeam Agent Deployment](agents_discovery_and_deployment.md)
* [Veeam Agent Backup Jobs and Policies](agents_job_mode.md)
* [Backup Chain](agents_backup_chain.md)
* [Backup of Microsoft Windows Computers](agents_backup_windows.md)
* [Backup of Linux Computers](agents_backup_linux.md)
* [Backup and Restore of Unix Computers](agents_backup_unix.md)
* [Backup of Mac Computers](agents_backup_mac.md)
* [Backup of Cloud Machines](agents_backup_cloud_machines.md)
* [Backup to Veeam Cloud Connect Repository](agents_cloud_connect.md)
* [Backup to Object Storage](agents_object_storage.md)
* [Backup to Deduplicating Storage Appliances](agents_deduplicating_storage.md)
* [Recovery Verification for Veeam Agent Backups](agents_recovery_verification.md)
* [Malware Detection](agents_malware_detection.md)


