---
title: "infrastructure_components"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/infrastructure_components.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---


In this article

To export backups created by Veeam Kasten policies using Veeam Plug-In for Kasten, you must configure the infrastructure that will consist of the following components:

1. Kasten application

A platform where you configure and manage Veeam Kasten policies that will export backups of application disks to Veeam backup repositories. For more information on installing a Kasten application, see [Veeam Kasten Docs](https://docs.kasten.io/latest/install/vmware/vsphere.html).

1. Veeam Backup & Replication server

A server that manages Veeam Kasten appliance and policies. It allows you to monitor and manage backups exported by Veeam Kasten, perform data protection scenarios, data recovery and restore operations. For more information, see the [Backup Server](https://helpcenter.veeam.com/docs/backup/vsphere/backup_server.html?ver=120) section in the Veeam Backup & Replication User Guide.

1. Veeam backup repository

This component is obligatory if you use Veeam backup repository to keep exports created by Veeam Kasten policies.

A storage location where Veeam Backup & Replication keeps backups exported by Veeam Kasten policies. You can add multiple repositories to the Veeam Backup & Replication server and set the necessary repository within Veeam Kasten policies settings.

To learn more about Veeam backup repositories and how to manage them, see the [Backup Repositories](https://helpcenter.veeam.com/docs/backup/vsphere/backup_repository.html?ver=120) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Note |
| We recommend that you use Veeam backup repositories that support the following file systems:   * ReFS for Microsoft Windows and SMB repositories * XFS for Linux repositories   You can also use backup repositories that utilize deduplication:   * Dell Data Domain with DD Boost * HPE StoreOnce with Catalyst  * ExaGrid Tiered Backup Storage * Quantum DXi * Fujitsu ETERNUS CS800 * Infinidat InfiniGuard |

|  |
| --- |
| Tip |
| To prohibit data deletion or data loss due to malware activity, you can make data stored in Veeam backup repositories immutable. Note that this option is available only for hardened repositories. For more information, see the [Hardened Repository](https://helpcenter.veeam.com/docs/backup/vsphere/hardened_repository.html?ver=120) section in the Veeam Backup & Replication User Guide. For more information on how to properly configure Veeam Kasten to make backups exported by Veeam Kasten policies immutable, see [Veeam Kasten Docs](https://docs.kasten.io/latest/usage/immutable.html#setting-up-immutable-backup-protection-using-veeam-backup-repository). |

1. Additional data protection layers

Veeam Backup & Replication allows you to keep backups exported by Veeam Kasten in the following types of additional repositories:

* Capacity tier: for more information, see the [Capacity Tier](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier.html?ver=120) section in the Veeam Backup & Replication User Guide.
* Archive tier: for more information, see the [Archive Tier](https://helpcenter.veeam.com/docs/backup/vsphere/archive_tier.html?ver=120) section in the Veeam Backup & Replication User Guide.

* Tape devices: for more information on how to back up to tapes, see the [Backup to Tape](https://helpcenter.veeam.com/docs/backup/vsphere/backup_to_tape_jobs.html?ver=120) section in the Veeam Backup & Replication User Guide.
* Cloud repositories of service providers that keep copies of backups exported by Veeam Kasten policies. For more information, see the [Veeam Cloud Connect Guide](https://helpcenter.veeam.com/docs/backup/cloud/cloud_overview.html?ver=120).
* Secondary Veeam backup repositories that keep backup copies created by backup copy jobs. For more information on backup copy jobs, see the [Backup Copy](https://helpcenter.veeam.com/docs/backup/vsphere/backup_copy.html?ver=120) section in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Important |
| Before you deploy the Veeam backup infrastructure, see the following [System Requirements](system_requirements.md). |

What You Do Next

[Deployment and Configuration](deployment.md)

Related Resources

* [Planning and Preparation](planning_and_preparation.md)

* [Backup Copy](https://helpcenter.veeam.com/docs/backup/vsphere/backup_copy.html?ver=120) in the Veeam Backup & Replication User Guide
* [Tape Devices Support](https://helpcenter.veeam.com/docs/backup/vsphere/tape_device_support.html?ver=120) in the Veeam Backup & Replication User Guide
* [Veeam Cloud Connect Infrastructure](https://helpcenter.veeam.com/docs/backup/cloud/cloud_infrastructure.html?ver=120) in the Veeam Cloud Connect User Guide

Page updated 3/17/2025

Page content applies to build 13.0.1.1071
