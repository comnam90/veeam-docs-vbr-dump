---
title: "Off-Host Backup Proxies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/offhost_backup_proxy.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# Off-Host Backup Proxies


An off-host backup proxy is a component that sits between the backup server and other backup infrastructure components in Microsoft Hyper-V environments. The proxy processes jobs and delivers backup traffic.

Usage Scenarios

An off-host backup proxy is required for off-host backup mode for Microsoft Hyper-V backup jobs. You can deploy an off-host backup proxy to remove unwanted overhead on the production Hyper-V host. In this case, the off-host backup proxy will retrieve VM data from the source datastore, process it and transfer it to the destination. For more information, see [Off-Host Backup](offhost_backup.md).

For more information on the backup infrastructure components required for different features, see feature descriptions.

Off-Host Backup Proxy Deployment

When you assign the role of an off-host backup proxy to the selected machine, Veeam Backup & Replication automatically installs on it light-weight components and services required for backup proxy functioning. Unlike the backup server, backup proxies do not require a dedicated SQL database — all settings are stored centrally, within the configuration database used by Veeam Backup & Replication.

|  |
| --- |
| Note |
| Versions of a Microsoft Hyper-V host and off-host backup proxy must coincide. For more information, see [System Requirements](system_requirements.md#offhost_proxy). |

Off-Host Backup Proxy Services

To enable a Hyper-V host or a Windows machine to act as an off-host backup proxy, Veeam Backup & Replication installs the following services on it:

* Veeam Installer Service is an auxiliary service that is installed and started on any Windows (or Hyper-V) server once it is added to the list of managed servers in the Veeam Backup & Replication console. This service analyzes the system, installs and upgrades necessary components and services.
* Veeam Data Mover Service/Veeam Transport Service is a service that performs data processing tasks on behalf of Veeam Backup & Replication, such as retrieving source VM data, performing data deduplication and compression, and storing backed-up data on the target storage.
* Veeam Hyper-V Integration Service is responsible for communicating with the VSS framework during backup, replication and other jobs, and performing recovery tasks. The service also deploys a driver that handles changed block tracking for Hyper-V.

General Requirements for Off-Host Backup Proxy

A machine performing the role of an off-host backup proxy must meet the following requirements:

* The machine must meet the system requirements. For more information, see [System Requirements](system_requirements.md#offhost_proxy).
* The role of an off-host backup proxy can be assigned only to a physical machine.

For evaluation and testing purposes, you can assign the off-host backup proxy role to a VM. To do this, you must enable the Hyper-V role on this VM (use nested virtualization). For more information, see [Nesting Hyper-V with VMware Workstation 8 and ESXi 5](https://www.veeam.com/blog/nesting-hyper-v-with-vmware-workstation-8-and-esxi-5.html) or [How to Install Hyper-V on a Virtual Machine in Hyper-V](http://blogs.technet.com/b/gbanin/archive/2013/06/26/how-to-install-hyper-v-on-a-virtual-machine-in-hyper-v.aspx) articles. However, it is not recommended that you use virtualized off-host backup proxies in the production environment.

* Before assigning the role of the off-host backup proxy to a machine, you must first add a Microsoft Hyper-V server to the backup infrastructure.

Requirements for Off-Host Backup Proxy and CSV (SAN) Storage

If you back up VMs located on a CSV (SAN) storage, a machine performing the role of an off-host backup proxy must meet the following requirements:

* If you plan to perform off-host backup for a Microsoft Hyper-V cluster with CSV, you must deploy an off-host backup proxy on a host that is not a part of the cluster. If the off-host backup proxy is deployed on a node of the cluster, the cluster will fail during VM data processing.
* The source Microsoft Hyper-V host and the off-host backup proxy must be connected to the shared storage through a SAN configuration. Make sure that the off-host backup proxy has read access to the storage LUNs.

* If you back up or replicate VMs whose disks reside on a CSV with Data Deduplication enabled, make sure that the versions of a Microsoft Hyper-V host and off-host backup proxy coincide and the Data Deduplication option is enabled on this off-host backup proxy. Otherwise, off-host backup will fail.

* To create and manage volume shadow copies on the shared storage, you must install and properly configure a VSS hardware provider that supports transportable shadow copies on the off-host proxy and each production Microsoft Hyper-V host. Typically, when configuring a VSS hardware provider, you need to specify a server controlling the LUN and disk array credentials to provide access to the array.

The VSS hardware provider is usually distributed as a part of client components supplied by the storage vendor. Any VSS hardware provider certified by Microsoft is supported. Some storage vendors may require additional software and licensing to work with transportable shadow copies.

Requirements for Off-Host Backup Proxy and SMB Shared Storage

If you back up VMs located on an SMB shared storage, a machine performing the role of an off-host backup proxy must meet the following requirements in addition to the general requirements listed earlier in this section:

* The off-host backup proxy must have read access to the SMB shared storage.
* The LocalSystem account of the off-host backup proxy must have read access permissions on the Microsoft SMB3 file share.

* The off-host backup proxy must be located in the same domain where the Microsoft SMB3 server resides. Alternatively, the domain where the Microsoft SMB3 server resides must be trusted by the domain in which the off-host backup proxy is located.

Limitations of Off-Host Backup Proxy

Do not use an off-host backup proxy to back up a VM with the VHD Set feature enabled. Otherwise, a backup job protecting such a VM will fail.

Related Topics

* [Adding Off-Host Backup Proxies Using Console](add_hyperv_proxy.md)
* [Adding Off-Host Backup Proxies Using Web UI](add_hyperv_proxy_web.md)
* [Editing Backup Proxy Settings](offhost_backup_proxy_edit.md)
* [Disabling and Removing Backup Proxies](offhost_setup_manproxy.md)
* [Configuring Advanced Options for Off-Host Backup Proxies](offhost_proxy_advanced.md)


