---
title: "Installing Veeam Plug-In for Xen Manually"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/xen_install_plugin.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Installing Veeam Plug-In for Xen Manually


The pre-installed plug-in that comes with the default installation package of Veeam Backup & Replication allows you to protect Xen resources. However, you may need to reinstall the plug-in on the Windows-based backup server in case it was deleted.

|  |
| --- |
| Note |
| If you use a remote Veeam Backup & Replication console, you do not need to install Veeam Plug-in for Xen on the workstation where the remote Veeam Backup & Replication console is deployed. |

To install Veeam Plug-in for Xen on a Windows-based backup server, do the following:

1. Log in to the backup server using an account with the local Administrator permissions.
2. Download a product installation file for Windows-based backup servers from your [Veeam download page](https://www.veeam.com/products/data-platform-trial-download.html?tab=virtualization-plugins).
3. Open the downloaded archive file and launch the installation file.

Before proceeding with installation, the installer will check whether you have Microsoft .NET Core Runtime installed on the backup server. In case the required version is missing, the installer will offer to install it automatically. To do that, click OK.

1. At the License Agreement step of the Veeam Plug-in for Xen setup wizard, read and accept the Veeam license agreement, licensing policy, the 3rd party components and required software license agreement. If you reject the agreements, you will not be able to continue installation.
2. At the Data Location step of the wizard, you can change the installation directory if necessary.
3. At the Ready to Install step of the wizard, click Install to begin installation.

Page updated 2026-07-30

