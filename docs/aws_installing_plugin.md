---
title: "Deploying Plug-In"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_installing_plugin.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Deploying Plug-In


If your installation package of Veeam Backup & Replication does not provide features that allow you to protect AWS resources, you must install Veeam Plug-in for AWS on the backup server to be able to add your backup appliances to the backup infrastructure.

|  |
| --- |
| Note |
| Before you install Veeam Plug-in for AWS, stop all running backup policies, disable all jobs, and close the Veeam Backup & Replication console. |

To install Veeam Plug-in for AWS, do the following:

1. Log in to the backup server using an account with the local Administrator permissions.
2. In a web browser, navigate to the [Veeam Backup & Replication: Download](https://www.veeam.com/backup-replication-vcp-download.html.) page, switch to the Cloud Plug-ins in the Additional Downloads section, and click the Download icon to download Veeam Plug-in for AWS.
3. Open the downloaded AWSPlugin\_13.11.x.x.zip file and launch the AWSPlugin\_13.11.x.x.zip installation file.
4. Complete the AWS Plug-In for Veeam Backup & Replication Setup wizard:

1. At the License Agreements step, read and accept the Veeam license agreement and licensing policy, as well as the license agreements of 3rd party components that Veeam incorporates, and the license agreements of required software. If you reject the agreements, you will not be able to continue installation.
2. At the Installation Path step of the wizard, you can specify the installation directory. To do that, click Browse. In the Browse for folder window, select the installation directory for the product or create a new one, and click OK.

1. At the Ready to Install step, click Install to begin installation.

[![Install Plug-in](images/aws_install_plugin.webp)](images/aws_install_plugin.webp "Install Plug-in")

Related Topics

* [Installing and Uninstalling Plug-In in Unattended Mode](aws_install_unattended.md)
* [Upgrading Plug-In](aws_upgrading_plugin.md)
* [Uninstalling Plug-In](aws_uninstall_plugin.md)

Page updated 2026-05-27

