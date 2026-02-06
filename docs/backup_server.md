---
title: "Backup Server"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_server.html"
last_updated: "2/5/2026"
product_version: "13.0.1.1071"
---

# Backup Server


The backup server is a Windows-based or Linux-based physical or virtual machine on which Veeam Backup & Replication is installed. It is the core component in the backup infrastructure that fills the role of the “configuration and control center”. The backup server performs all types of administrative activities:

* Coordinates backup, replication, recovery verification and restore tasks.
* Controls job scheduling and resource allocation.
* Is used to set up and manage backup infrastructure components as well as specify global settings for the backup infrastructure.

In addition to its primary functions, a newly deployed backup server also performs the following roles:

* [For VMware vSphere] the default VMware backup proxy and the backup repository (it manages data handling and data storing tasks).
* [For Microsoft Hyper-V] the default backup repository, storing backups locally.

|  |
| --- |
| Important |
| The backup server cannot be added as a managed server to another Veeam Backup & Replication server. This type of deployment is unsupported and may cause issues in Veeam services coordination. |

Related Topics

* [Veeam Software Appliance Installation](deployment_linux.md)
* [Veeam Backup & Replication Installation on Microsoft Windows](installation.md)
* [Veeam Backup & Replication Services](services_and_components.md)


