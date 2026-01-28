---
title: "Plug-in Deployment"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/vsphere_plugin_deployment.html"
last_updated: "1/27/2026"
product_version: "13.0.1.1071"
---

# Plug-in Deployment


Veeam Plug-in for VMware vSphere Client is installed remotely on the Veeam Backup Enterprise Manager server. During deployment, the installer registers the plug-in as an extension on the VMware vCenter Server, and the vCenter Server downloads the plug-in manifest file. This allows the vsphere-ui service to define how the plug-in extends the VMware vSphere Client user interface. The back-end service of the plug-in runs on the Enterprise Manager server.

You can install Veeam Plug-in for VMware vSphere Client using Veeam Backup Enterprise Manager under an account with the Portal Administrator role. For more information, see [Installing vSphere Client Plug-in](vsphere_plugin_installing.md).

For more information on VMware vSphere Client, see the [vCenter and Host Management](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/vcenter-and-host-management-8-0.html) section of the VMware vSphere documentation.

Before you install the plug-in, make sure the following requirements are met:

* The plug-in supports vSphere Client version 7.0.1 and later.

* The vCenter Server must be added to the backup server infrastructure.

For more information, see the [Adding VMware vSphere Servers](https://helpcenter.veeam.com/docs/vbr/userguide/add_vmware_server.html?ver=13) section of the Veeam Backup & Replication User Guide.

* The backup server that contains the vCenter Server in its infrastructure must be connected to Enterprise Manager.

For more information, see [Adding Backup Servers](adding_backup_server.md).

* The Enterprise Manager server must be able to resolve the FQDN of the vCenter Server and must have access to the vCenter Server over HTTPS. In particular, this is necessary if the plug-in uses the default vCenter Single Sign-On for authentication.
* Account used to install the plug-in must have sufficient access rights for vCenter Server:

* Extension > Register extension — to install the plug-in
* Extension > Unregister extension — to uninstall the plug-in

The account must belong to the same domain as the vCenter Server in case of cross-domain access.

* Note that when accessing VMware vSphere Client, you must enter the vCenter Server FQDN (or IP address) that you specified when adding the vCenter Server to the backup server infrastructure. This FQDN is stored in the configuration database and used to authenticate the vCenter Server. vCenter Server alias names are not supported.


