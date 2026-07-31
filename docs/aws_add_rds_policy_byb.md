---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_rds_policy_byb.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before you protect RDS resources, consider the following:

* If you plan to create image-level backups of RDS resources, backup infrastructure components that will take part in the backup process must be added to the backup infrastructure and configured properly. These include [backup repositories](aws_repositories_add_ui.md) and [worker instances](aws_workers.md).

* Veeam Plug-in for AWS supports creating image-level backups for Microsoft SQL Server and PostgreSQL DB instances only. However, the size of each database hosted on a protected Microsoft SQL Server DB instance must not exceed 5 TiB.

For the list of supported PostgreSQL versions, see [Protecting RDS Resources](aws_overview_rds.md#applications).

* For backup appliances to be able to create image-level backups for PostgreSQL DB instances, make sure that [security groups associated with worker instances](aws_worker_add_config_prod.md#region) allow outbound HTTPS traffic from the worker instances through port 443 to download a certificate bundle for establishing SSL/TLS connections. For more information on certificate bundles for AWS Regions, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.SSL.html#UsingWithRDS.SSL.RegionCertificates).
* Veeam Plug-in for AWS does not support creating cloud-native snapshots for PostgreSQL DB clusters with Multi-AZ DB cluster deployment and IBM Db2 DB instances.
* Veeam Plug-in for AWS does not support creating cloud-native snapshots for Aurora PostgreSQL Limitless Database clusters.
* Veeam Plug-in for AWS does not support creating image-level backups for Microsoft SQL Server DB instances that host system databases only.
* Veeam Plug-in for AWS does not support creating image-level backups for Aurora PostgreSQL clusters.
* Veeam Plug-in for AWS does not support creating archived backups for Microsoft SQL Server DB instances.

* [Applies only if you plan to back up Microsoft SQL Server DB instances] The SQLSERVER\_BACKUP\_RESTORE option must be added to the option group that is applied to each processed DB instance.

The IAM role that is associated with the SQLSERVER\_BACKUP\_RESTORE option must have the permissions required to access temporary Amazon S3 buckets. The IAM role must also have a trust relationship and a permissions policy attached to allow the Amazon RDS service to assume the role. For more information on the backup and restore option, see [AWS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Appendix.SQLServer.Options.BackupRestore.html#Appendix.SQLServer.Options.BackupRestore.Add).

* [Applies only if you plan to back up Microsoft SQL Server DB instances] If you plan to enable the [private network deployment](aws_enable_private_network_deployment.md) functionality, backup appliances must be able to connect to the public s3.<region>.amazonaws.com endpoint to access temporary Amazon S3 buckets. Otherwise, backup policies processing DB instances will fail to produce image-level backups. For more information on the temporary buckets, see [Performing RDS Backup](aws_backup_hiw_rds.md).

* Veeam Plug-in for AWS runs retention sessions at 4:00 AM by default, according to the time zone set on the backup appliance. If you schedule backup policies to execute at 4:00 AM, the backup policies and retention tasks will be queued.

Page updated 2026-05-21

