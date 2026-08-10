---
title: "Overview"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_welcome.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Overview


Starting from backup appliance version 7.0, Veeam Plug-in for AWS is part of the Veeam Backup & Replication solution. Veeam Plug-in for AWS extends the Veeam Backup & Replication functionality and allows you to add backup appliances to Veeam Backup & Replication. With Veeam Plug-in for AWS, you can manage data protection and recovery operations for all these appliances from a single Veeam Backup & Replication console.

Backup appliance versions 7.0, 8.0, 9.0 and 10 come with 6 major features — the ability to create image-level backups of Microsoft SQL Server and PostgreSQL DB instances, as well as the ability to back up DynamoDB tables, Redshift clusters, Redshift Serverless namespaces and FSx file systems. These features are available only for backup appliances managed by a Veeam Backup & Replication server. To unlock the full functionality, [install Veeam Plug-in for AWS on the server](aws_deployment.md) and [add your appliances](aws_connect_appliance.md) to the backup infrastructure.

|  |
| --- |
| Note |
| The current version of the Veeam Backup & Replication console comes with Veeam Plug-in for AWS pre-installed by default. For the list of compatible versions of Veeam Backup & Replication, see [System Requirements](aws_system_requirements.md#versions). |

Considerations and Limitations

Before you add backup appliances to the backup infrastructure, consider the following:

* If you remove a backup appliance from the backup infrastructure, the following will happen:

* You will no longer be able to create image-level backups of Microsoft SQL Server and PostgreSQL DB instances, and the existing RDS backup policies configured to create these backups will start failing. To work around the issue, you can disable image-level backup when [editing backup policy settings](aws_policies_edit.md).

* You will no longer be able neither to add and start DynamoDB, FSx, Redshift Clusters and Redshift Serverless backup policies, nor to manually back up DynamoDB tables, FSx file systems, Redshift clusters and Redshift Serverless namespaces.

* If the connection between a backup appliance and the backup server is lost for more than 31 days, the appliance will enter the standalone mode, and you will no longer be able to back up Microsoft SQL Server instances, PostgreSQL DB instances, DynamoDB tables, FSx file systems, Redshift clusters and Redshift Serverless namespaces.

Related Topics

* [Protecting RDS Resources](aws_overview_rds.md)
* [Protecting DynamoDB Tables](aws_overview_dynamo.md)
* [Protecting Redshift Clusters](aws_overview_redshift.md)
* [Protecting Redshift Serverless](aws_overview_redshift_serverless.md)
* [Protecting FSx File Systems](aws_overview_fsx.md)

Page updated 2026-06-29

