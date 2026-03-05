---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_limitations.html"
last_updated: "2/26/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


Coexistence with Mission-Critical Production Servers

We do not recommend you to install Veeam Backup & Replication and its components on mission-critical machines in the production environment such as vCenter Server, Microsoft Hyper-V Server, Domain Controller, Microsoft Exchange Server, Windows Server Essentials and so on. If possible, install Veeam Backup & Replication and its components on dedicated machines. Backup infrastructure component roles can be co-installed.

Microsoft Windows Server Core

You can assign roles of a backup proxy, backup repository, WAN accelerator, Veeam Cloud Connect infrastructure components and tape infrastructure components to machines running Microsoft Windows Server Core.

Windows Server IoT/Windows Storage Server Support

For information about support of Windows Server IoT/Windows Storage Server, see [this Veeam KB article](https://www.veeam.com/kb1923).

Domain Member

The machine on which you plan to install Veeam Backup & Replication does not necessarily need to be a domain member. However, if you plan to restore Microsoft Exchange items from the Veeam Backup Enterprise Manager UI, you must install Veeam Backup Enterprise Manager on the domain member server from the Microsoft Active Directory forest in which Microsoft Exchange mailboxes are located.

All-in-One Installations

For [all-in-one installations](simple.md), you can subtract 2 GB of memory resources from each but one role. These 2 GB are allotted to the OS itself, assuming each component is installed on the dedicated server.

Sharing Backup Infrastructure Components Across Veeam Installations

Using Linux-based shared backup infrastructure components across different Veeam installations is not supported.

As for non-Linux backup infrastructure components, we do not recommend using them shared across different Veeam installations due to several reasons:

* Veeam installations compete for resources.
* Backup components cannot simultaneously interact with Veeam Backup & Replication of different versions.
* Adding the same repository to different Veeam Backup & Replication installations may lead to corrupted backup and data in the database.

Native Hyper-V Replication

Do not use native Hyper-V replication especially if replication is targeted at the same scope (host, cluster, SCVMM) where the source VM resides. This can cause VM ID collision. Instead, we recommend you use Veeam replication. For more information, see [Replication](replication.md).

Unstructured Data Backup

Each of the following components for unstructured data backup may consume up to 4 GB RAM per task (in case of deduplicating storage appliances, up to 8 GB RAM): [backup repository](#repo), [general-purpose backup proxy](#file_proxy), [cache repository](#cache_repo). Make sure you allocate enough memory resources for your installation. For all-in-one installations, where the server performs several roles, it must have enough memory resources for all components.

Network Limitations

Consider the following requirements and limitations:

* Names of port groups/segments/networks must be unique.

* [For VMware vSphere] VMware NSX-T 2.3 or later is supported with N-VDS for VMware vSphere and VMware Cloud on AWS/Dell.
* [For VMware vSphere] VMware NSX-T 3.0 or later is supported with VDS for VMware vSphere and VMware Cloud on AWS/Dell.
* [For VMware vSphere] VMware NSX-V is supported (see details on the support of vSphere and VMware Cloud version in [VMware vSphere Virtual Infrastructure](#vm_virt_infrastructure)).


