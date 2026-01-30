---
title: "Virtualization Servers and Hosts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/setup_add_server.html"
last_updated: "11/26/2025"
product_version: "13.0.1.1071"
---

# Virtualization Servers and Hosts


You can add the following types of servers and hosts to the backup infrastructure:

* [VMware vSphere Server](add_vmware_server.md)
* [VMware Cloud Director](adding_vcloud_director.md)
* [Microsoft Hyper-V Server](add_hyperv_server.md)
* [Microsoft SMB3 Server](smb.md)
* [Microsoft Windows Server](add_windows_server.md)
* [Linux Server](add_linux_server.md)

|  |
| --- |
| Note |
| We recommend that only one instance of a server or host is present in the backup infrastructure at a time. Do not add the same server or host multiple times, for example, by a DNS name and an IP address or an alternative IP address, this can cause unexpected behavior. |

You can add physical machines and VMs to the backup infrastructure and assign different roles to them. The following table describes which roles can be assigned to the different types of servers in VMware vSphere environments.

| Server Type | Source Host | Target Host | Backup Proxy | Backup Repository |
| --- | --- | --- | --- | --- |
| VMware vSphere Server  (standalone ESXi host or vCenter Server) | ✓ | ✓ | ✕ | ✕ |
| VMware Cloud Director | ✓ | ✓  (for Cloud Director replication and continuous data protection) | ✕ | ✕ |
| Microsoft Windows server | ✕ | ✕ | ✓ | ✓ |
| Linux server | ✕ | ✕ | ✓ | ✓ |

The following table describes which roles can be assigned to the different types of servers in Microsoft Hyper-V environments.

| Server Type | Source Host | Target Host | Off-Host Backup Proxy | Backup Repository |
| --- | --- | --- | --- | --- |
| Microsoft Hyper-V Server  (standalone Microsoft Hyper-V host, SCVMM or Hyper-V cluster) | ✓ | ✓ | ✕ | ✓ |
| Microsoft SMB3 server | ✓ | ✕ | ✕ | ✕ |
| Microsoft Windows server | ✕ | ✕ | ✓ | ✓ |
| Linux server | ✕ | ✕ | ✕ | ✓ |

|  |
| --- |
| Note |
| You can also add the following servers:   * Hyper-V servers. For more information on how to add servers, see the [Adding Microsoft Hyper-V Servers](add_hyperv_server.md) section in the Veeam Backup & Replication User Guide. * VMware vSphere servers. For more information on how to add servers, see the [Adding VMware vSphere Servers](add_vmware_server.md) section in the Veeam Backup & Replication User Guide. * Proxmox VE servers (standalone hosts and clusters). For more information on how to add servers, see the [Connecting Proxmox VE Server](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/connecting_manager.html?ver=3) section in the Proxmox VE User Guide. * Kasten instances. For more information on how to add Kasten instances, see the [Deployment and Configuration](https://helpcenter.veeam.com/docs/vbr/kasten_integration/deployment.html?ver=13) section in the Veeam Kasten Integration Guide. * Nutanix AHV servers (standalone clusters and Prism Centrals). For more information on how to add AHV servers, see the [Connecting Nutanix AHV Server](https://helpcenter.veeam.com/docs/vbahv/userguide/managing_clusters.html?ver=9) section in the Veeam Plug-In for Nutanix AHV User Guide. * oVirt KVM managers\*. For more information on how to add oVirt KVM managers see the [Connecting oVirt KVM Manager](https://helpcenter.veeam.com/docs/vbrhv/userguide/connecting_manager.html?ver=7) section in the Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization User Guide. * Veeam Backup for AWS servers. For more information on how to add servers, see the [Connecting to Existing Appliances](https://helpcenter.veeam.com/docs/vbaws/guide/connect_appliance.html?ver=10) section in the Veeam Backup for AWS User Guide. * Veeam Backup for Microsoft Azure servers. For more information on how to add servers, see the [Connecting to Existing Appliances](https://helpcenter.veeam.com/docs/vbazure/guide/connecting_appliance_console.html?ver=8.1) section in the Veeam Backup for Microsoft Azure User Guide. * Veeam Backup for Google Cloud servers\*. For more information on how to add servers, see the [Connecting to Existing Appliances](https://helpcenter.veeam.com/docs/vbgc/guide/connecting_existing_appliance.html?ver=7) section in the Veeam Backup for Google Cloud Guide.   \*This feature is available for Microsoft Windows-based backup servers. |

Related Topics

* [Veeam Data Mover Service](veeam_transport_service.md)
* [Rescanning Servers](servers_rescan.md)
* [Editing Server Settings](edit_server.md)
* [Removing Servers](remove_server.md)


