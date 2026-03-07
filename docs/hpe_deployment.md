---
title: "Deployment"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hpe_deployment.html"
last_updated: "3/5/2026"
product_version: "13.0.1.1071"
---

# Deployment


The default installation package of Veeam Backup & Replication does not provide features that allow you to protect HPE Morpheus VM Essentials resources. To be able to add HPE Morpheus VM Essentials servers and workers to the backup infrastructure, you must install Veeam Plug-in for HPE Morpheus VM Essentials on the backup server.

|  |
| --- |
| Tip |
| If you use a remote Veeam Backup & Replication console, you do not need to install Veeam Plug-in for HPE Morpheus VM Essentials on the workstation where the remote Veeam Backup & Replication console is deployed. |

Installing Plug-In on Windows-Based Backup Server

If the backup server runs on a Windows-based machine, do the following:

1. Log in to the backup server using an account with the local Administrator permissions.
2. Download the product installation file for Windows-based backup servers from the [Veeam download page](https://www.veeam.com/products/data-platform-trial-download.html?tab=virtualization-plugins).
3. Open the downloaded .ZIP file and launch the .EXE installation file.

|  |
| --- |
| Note |
| Before proceeding with installation, the installer will check whether you have Microsoft .NET Core Runtime installed on the backup server. In case the required version is missing, the installer will offer to install it automatically. To do that, click OK. |

1. Complete the installation wizard:

1. At the License Agreement step, read and accept the Veeam license agreement, licensing policy, the 3rd party components and required software license agreements. If you reject the agreements, you will not be able to continue installation.
2. At the Data Location step, you can change the installation directory if necessary.
3. At the Ready to Install step, click Install to begin installation.

Installing Plug-In on Linux-Based Backup Server

If the backup server runs on a Linux-based machine, do the following:

1. Download the product installation file for Linux-based backup servers from the [Veeam download page](https://www.veeam.com/products/data-platform-trial-download.html?tab=virtualization-plugins).
2. Log in to the Host Management web console as described in section [Accessing Host Management Console](hmc_access.md).
3. In the web console, navigate to Logs and Services > Components and click Add Component. Then, upload the installation file:

1. Click Browse, select the necessary file and then click Upload.
2. After the file is uploaded, read the Veeam license agreement, licensing policy, the 3rd party components and required software license agreements. Then, click Install Now to acknowledge the agreements and begin installation.


