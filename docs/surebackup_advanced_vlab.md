---
title: "Advanced Single-Host Virtual Labs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_advanced_vlab.html"
last_updated: "4/29/2025"
product_version: "13.0.1.1071"
---

# Advanced Single-Host Virtual Labs

In this article

The advanced single-host virtual lab can be used if VMs that you want to verify and VMs from the application group are connected to different networks.

In the advanced single-host virtual lab, Veeam Backup & Replication creates several virtual networks for the virtual lab. The number of virtual networks corresponds to the number of production networks to which verified VMs are connected. Networks in the virtual lab are mapped to production networks.

Veeam Backup & Replication automatically adds a number of new VMware objects on the ESXi host where the virtual lab is created:

* A resource pool
* A VM folder
* A standard vSwitch

The vSwitch is only used by the VMs started in the virtual lab. There is no routing outside the virtual lab to other networks.

When you create an advanced single-host virtual lab, Veeam Backup & Replication configures basic settings for networks that are created in the virtual lab. You need to review these settings and manually adjust them.

![Advanced Single-Host Virtual Labs](images/advanced_vlab_vsphere.webp)

Page updated 4/29/2025

Page content applies to build 13.0.1.1071
