---
title: "Deploying Plug-In"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_deploying_plug_in.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Deploying Plug-In


If your installation package of Veeam Backup & Replication does not provide features that allow you to protect Azure resources, you must install Veeam Plug-in for Microsoft Azure on the backup server to be able to add your backup appliances to the backup infrastructure.

|  |
| --- |
| Note |
| Before you install Veeam Plug-in for Microsoft Azure, stop all running backup policies, disable all jobs, and close the Veeam Backup & Replication console. |

To install Veeam Plug-in for Microsoft Azure, do the following:

1. Log in to the backup server using an account with the local Administrator permissions.
2. In a web browser, navigate to the [Veeam Backup & Replication: Download](https://www.veeam.com/backup-replication-vcp-download.html.) page, switch to the Cloud Plug-ins in the Additional Downloads section, and click the Download icon to download Veeam Plug-in for Microsoft Azure.
3. Open the downloaded MicrosoftAzurePlugin\_13.9.0.354.zip file and launch the MicrosoftAzurePlugin\_13.9.0.354.exe installation file.
4. Complete the Microsoft Azure Plug-in for Veeam Backup & Replication wizard:

1. At the License Agreements step, read and accept the Veeam license agreement and licensing policy, as well as the license agreements of 3rd party components that Veeam incorporates, and the license agreements of required software. If you reject the agreements, you will not be able to continue installation.
2. At the Installation Path step, you can specify the installation directory. To do that, click Browse. In the Browse for folder window, select the installation directory for the product or create a new one, and click OK.
3. At the Ready to Install step, click Install to begin installation.

![Deploying Plug-In](images/azure_install.webp)

In This Section

* [Installing Plug-In in Unattended Mode](azure_installing_plug_in_unattended.md)

Page updated 2026-07-31

