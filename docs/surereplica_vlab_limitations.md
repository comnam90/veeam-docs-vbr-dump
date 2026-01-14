---
title: "Limitations of Single-Host Virtual Labs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surereplica_vlab_limitations.html"
last_updated: "8/16/2024"
product_version: "13.0.1.1071"
---

# Limitations of Single-Host Virtual Labs

In this article

If VM replicas are located on different hosts, you cannot use the single-host virtual lab configuration (basic or advanced). A single-host virtual lab uses standard vSwitches that have specific configuration limitations.

When you create or edit a virtual lab, Veeam Backup & Replication creates a new port group for each isolated network in the virtual lab. All VMs in the isolated network are added to this port group. Such configuration helps differentiate the traffic passing through the standard vSwitch to the isolated network in the virtual lab.

However, the standard vSwitch has a restriction: it is “limited” to one ESXi host. A standard vSwitch is configured on a specific ESXi host. The configuration of the standard vSwitch, such as information about port groups, resides on the ESXi host where the vSwitch is configured. Other ESXi hosts in the virtual environment do not have access to this information.

![Limitations of Single-Host Virtual Labs](images/standard_vswitch.webp)

For this reason, the single-host configuration can only be used if all VM replicas are registered on the same ESXi host. If attempt to verify VM replicas registered on different ESXi hosts in the single-host virtual lab, VMs from different port groups will not be able to “see” each other and communicate with each other.

To overcome this limitation and verify VM replicas that are registered on different ESXi hosts, you can use [advanced multi-host virtual labs](surereplica_advanced_mutihost.md).

Page updated 8/16/2024

Page content applies to build 13.0.1.1071
