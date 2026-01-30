---
title: "Backup Target"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_system_requirements_backup_target.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Backup Target


Backup can be performed to the storage targets listed below.

Veeam Agent Backup Jobs Managed by Backup Server

If you protect Veeam Agent computers by a backup job managed by Veeam backup server, you can store backups in the following types of repositories.

* Veeam Backup & Replication version 13.0.1 backup repository
* Veeam Cloud Connect 13.0.1 cloud repository

Veeam Agent Backup Jobs Managed by Veeam Agent

If you protect Veeam Agent computers by a backup job managed by Veeam Agent, you can store backups in repositories configured in the following locations:

* Local (internal) storage of the protected computer (not recommended)
* Direct attached storage (DAS), such as USB, eSATA or Firewire external drives, and raw device mapping (RDM) volumes

|  |
| --- |
| IMPORTANT |
| [For Veeam Agent for Microsoft Windows] Storage devices with the exFAT file system are not supported as a backup target. |

* Network Attached Storage (NAS) able to represent itself as an SMB (CIFS) share
* Network Attached Storage (NAS) able to represent itself as an NFS share (for backups of Linux and Unix computers only)
* On-premises and cloud-based object storage (except backups of Unix computers)
* Veeam Backup & Replication version 13.0.1 backup repository
* Veeam Cloud Connect 13.0.1 cloud repository

|  |
| --- |
| IMPORTANT |
| Veeam Cloud Connect repository is not supported as a backup and backup copy target for the following Veeam Agents:   * Veeam Agent for IBM AIX * Veeam Agent for Oracle Solaris * Veeam Agent for Linux on Power |


