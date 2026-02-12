---
title: "Installing Veeam Plug-in for Scale Computing HyperCore Manually"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_install_plugin.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Installing Veeam Plug-in for Scale Computing HyperCore Manually


[This section applies only to Windows-based backup servers]

The pre-installed plug-in that comes with the default installation package of Veeam Backup & Replication allows you to protect Scale Computing HyperCore resources. However, you may require to install a new plug-in version on the backup server manually if some updates and patches become available.

|  |
| --- |
| Note |
| If you use a remote Veeam Backup & Replication console, you do not need to install Veeam Plug-in for Scale Computing HyperCore on the workstation where the remote Veeam Backup & Replication console is deployed. |

To install Veeam Plug-in for Scale Computing HyperCore, do the following:

1. Log in to the backup server using an account with the local Administrator permissions.
2. Download a product installation file from your [Veeam account page](https://my.veeam.com).
3. Open the downloaded archive file and launch the installation file.

Before proceeding with installation, the installer will check whether you have Microsoft .NET Core Runtime installed on the backup server. In case the required version is missing, the installer will offer to install it automatically. To do that, click OK.

1. At the License Agreement step of the Veeam Plug-in for Scale Computing HyperCore Setup wizard, read and accept both the Veeam license agreement, licensing policy, the 3rd party components and required software license agreement. If you reject the agreements, you will not be able to continue installation.

To read the documents included in the agreement, click the links of the documents.

![Installing Veeam Plug-in for Scale Computing HyperCore Manually](images/sch_install_plugin_agreement.webp "Installing RHV Plug-In")

1. At the Data Location step of the wizard, you can change the installation directory if necessary.

![Installing Veeam Plug-in for Scale Computing HyperCore Manually](images/sch_install_plugin_custom.webp "Installing RHV Plug-In")

1. Click Install to begin installation.

![Installing Veeam Plug-in for Scale Computing HyperCore Manually](images/sch_install_plugin_ready.webp "Installing RHV Plug-In")


