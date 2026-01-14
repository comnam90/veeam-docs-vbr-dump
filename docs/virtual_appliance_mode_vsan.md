---
title: "Virtual Appliance Mode for VMs on VSAN"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/virtual_appliance_mode_vsan.html"
last_updated: "10/14/2025"
product_version: "13.0.1.1071"
---

# Virtual Appliance Mode for VMs on VSAN

In this article

To transport data of VMs residing on VSAN in the Virtual appliance mode, you must assign the VMware backup proxy role to a VM.

The VMware backup proxy VM must meet the following requirements:

* The VMware backup proxy VM must reside on an ESXi host connected to a VSAN cluster.

Veeam Backup & Replication will retrieve data of processed VMs over the I/O stack of the ESXi host on which the VMware backup proxy is deployed.

* Disks of the VMware backup proxy VM must reside on the VSAN datastore.

If you have several backup proxies on ESXi hosts in the VSAN cluster, Veeam Backup & Replication chooses the most appropriate VMware backup proxy to reduce the backup traffic on the VSAN cluster network. To choose a VMware backup proxy, Veeam Backup & Replication checks HDDs directly attached to every ESXi host and calculates the amount of VM data on these HDDs. The preference is given to the ESXi host that has a direct access to an HDD with the maximum amount of VM data. This approach helps reduce workload on the ESXi I/O stack during data transport.

If you notice excessive network link utilization during backup operations, consider the following:

* Create one VMware backup proxy VM for each ESXi host in the VSAN cluster to reduce the workload on the ESXi I/O stack during backup.
* Consider creating a VM-Host affinity rule to prevent the VMware backup proxy from being moved off its assigned ESXi host. For more information on how to create VM-Host affinity rules, see [VMware Docs](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/vsphere-resource-management-8-0/using-drs-clusters-to-manage-resources/create-a-vm-host-affinity-rule.html).

|  |
| --- |
| Note |
| Even if disks of a VM are located on a host where the VMware backup proxy is deployed, VSAN traffic may still be observed between hosts in the cluster. This behavior depends on the VSAN cluster itself and cannot be modified in Veeam Backup & Replication. |

Page updated 10/14/2025

Page content applies to build 13.0.1.1071
