---
title: "Veeam Plug-in for VMware vSphere Client Authentication"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/remote_vsphere_client_plugin.html"
last_updated: "1/27/2026"
product_version: "13.0.1.1071"
---

# Veeam Plug-in for VMware vSphere Client Authentication


Veeam Plug-in for VMware vSphere Client is installed remotely on the Veeam Backup Enterprise Manager server. During deployment, the installer registers the plug-in as an extension on the VMware vCenter Server, and the vCenter Server downloads the plug-in manifest file. This allows the vsphere-ui service to define how the plug-in extends the VMware vSphere Client user interface. The back-end service of the plug-in runs on the Enterprise Manager server.

When using the plug-in, the authentication process includes the following steps:

1. You log in to VMware vSphere Client. To work with the Veeam Plug-in for VMware vSphere Client, your user account must belong to a vCenter Server role that is mapped to an Enterprise Manager role. For more information on role mapping, see [Configuring VMware vSphere Roles](configuring_vmware_vsphere_roles.md).

* To create a VeeamZIP backup or Quick Backup, the Portal Administrator or Portal User role is required.

* To browse backup infrastructure, the Restore Operator role is enough.

[Optional] If you have Veeam ONE deployed in your environment and you want to open Veeam ONE reports from the plug-in, the accounts used to log in to the VMware vSphere Client must be also included in the Veeam ONE Power Users, Veeam ONE Read-Only Users or Veeam ONE Administrators group on the machine where Veeam ONE Server is installed. For more information, see the [Security Groups](https://helpcenter.veeam.com/docs/one/userguide/security_groups.html?ver=13) section of the Veeam ONE Deployment Guide.

1. Veeam Plug-in for VMware vSphere Client connects to Enterprise Manager, and Enterprise Manager verifies the user account. To perform VeeamZIP and Quick Backup operations, the user account must have the following permissions at the vCenter level: VirtualMachine.Interact.Backup, Task.Create, Task.Update.

[![Authentication Process](images/remote_vsphere_client_plugin.webp)](images/remote_vsphere_client_plugin.webp "Authentication Process")


