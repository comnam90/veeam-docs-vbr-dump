---
title: "Deploying Tenant Veeam Backup Server"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_user_vbr_deploy.html"
last_updated: "11/11/2025"
product_version: "13.0.1.1071"
---


In this article

To deploy the tenant Veeam backup server, you must install Veeam Backup & Replication on a Microsoft Windows server on your side.

The installation process of Veeam Backup & Replication in the Veeam Cloud Connect infrastructure is the same as the installation process in a regular Veeam backup infrastructure. To learn more about system requirements, required permissions and the installation process workflow, see the [Deployment](https://helpcenter.veeam.com/docs/vbr/userguide/deployment.html?ver=13) section in the Veeam Backup & Replication User Guide.

In addition to requirements listed in the product documentation, the tenant Veeam backup server must meet the following requirements:

* The tenant Veeam backup server must have any type of paid license installed. The Community edition of Veeam Backup & Replication does not support the Veeam Cloud Connect functionality. That is, you cannot create backup and replication jobs targeted at cloud resources of the SP; data recovery operations from the cloud are supported.
* The tenant Veeam backup server must have access to all components that will take part in data protection and disaster recovery tasks. These include a gateway server configured on the SP side, source virtualization hosts and source WAN accelerator (optional).

Page updated 11/11/2025

Page content applies to build 13.0.1.1071
