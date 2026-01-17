---
title: "Deployment and Configuration"
product: "vbr"
doc_type: "kasten_integration"
source_url: "https://helpcenter.veeam.com/docs/vbr/kasten_integration/deployment.html"
last_updated: "8/26/2024"
product_version: "13.0.1.1071"
---

# Deployment and Configuration


To be able to protect data with the Veeam Plug-In for Kasten solution, you must configure the Veeam Kasten instance and Veeam Backup & Replication infrastructure.

Configure Kasten Instance Infrastructure

A Veeam Kasten instance is a source environment that creates snapshots of applications running on Kubernetes persistent volumes. After that, Veeam Kasten makes exports of snapshot data to storage locations to keep this data. As a storage location, you can use Veeam backup repositories where the application persistent volumes are stored in a native Veeam format. While Veeam Kasten stores the persistent volume's images in the Veeam backup repository, it still requires a primary location to store any file based data and metadata. This location can be any additional storage type supported by Veeam Kasten, such as object storage or NFS.

The Veeam Kasten instance you plan to use in the Veeam Plug-In for Kasten infrastructure must meet the [system requirements](system_requirements.md#k10). For more information on configuring the Veeam Kasten instance, see [Veeam Kasten Docs](https://docs.kasten.io/latest/install/vmware/vsphere.html#installing-k10-on-vmware-vsphere).

Configure Veeam Backup & Replication Infrastructure

To configure Veeam Backup & Replication infrastructure, complete the following steps:

1. Install or upgrade Veeam Backup & Replication.

After you install Veeam Backup & Replication, Veeam Plug-In for Kasten will be automatically installed along with Veeam Backup & Replication.

1. Add Kasten instance.

Add the Kasten instance to the Veeam Backup & Replication infrastructure to be able to create and manage Kasten policies. For more information, see [Adding Kasten Instance](adding_k10.md).

1. [Optional] Deploy Veeam backup repositories.

If you want to keep persistent volumes created by Veeam Kasten policies in Veeam backup repositories, you must add the Veeam backup repositories that will store backups exported by Veeam Kasten policies to Veeam Backup & Replication infrastructure. Make sure that you configured the [required permissions](req_permissions.md). For more information, see the [Backup Repositories](https://helpcenter.veeam.com/docs/backup/vsphere/backup_repository.html?ver=120) and [Adding Microsoft Windows Repositories](https://helpcenter.veeam.com/docs/backup/vsphere/repo_add.html?ver=120) sections in the Veeam Backup & Replication User Guide.

1. [Optional] Configure capacity and archive tier.

Configure the capacity tier and archive tier to set an additional layer of storage. For more information, see [Capacity Tier](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier.html?ver=120) and [Archive Tier](https://helpcenter.veeam.com/docs/backup/vsphere/archive_tier.html?ver=120) sections in the Veeam Backup & Replication User Guide.

1. [Optional] Configure Tape infrastructure.

If you want to use tape devices to store Kubernetes persistent volumes. For more information, see the [Tape Devices Support](https://helpcenter.veeam.com/docs/backup/vsphere/tape_device_support.html?ver=120) section in the Veeam Backup & Replication User Guide.

1. [Optional] Configure Cloud Connect infrastructure.

If you want to store copies of backed-up Kubernetes persistent volumes in cloud repositories of service providers, configure Cloud Connect infrastructure in a Veeam Backup & Replication console. For more information, see [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/backup/cloud/cloud_overview.html?ver=120) User Guide.

|  |
| --- |
| Note |
| The additional level of protection (that is, capacity and archive tier, tape devices and cloud repositories of service providers) is available only if you export Kasten backups to the Veeam backup repository. |

What You Do Next

After you configure the Veeam Kasten instance and add it to the Veeam Backup & Replication infrastructure, you are ready to [create Veeam Kasten policies](add_policy.md) and perform data protection and data recovery options.

In This Section

* [Installing Plug-in](installing_plugin.md)
* [Adding Kasten Instance](adding_k10.md)
* [Managing Kasten Instance](managing_instance.md)


