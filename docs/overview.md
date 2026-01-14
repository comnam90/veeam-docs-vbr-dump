---
title: "About Veeam Backup & Replication"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/overview.html"
last_updated: "12/30/2025"
product_version: "13.0.1.1071"
---

# About Veeam Backup & Replication

In this article

Veeam Backup & Replication is a comprehensive data protection and disaster recovery solution. With Veeam Backup & Replication, you can create image-level backups of virtual, physical and cloud machines and restore from them. Technology used in the product optimizes data transfer and resource consumption, which helps to minimize storage costs and the recovery time in case of a disaster.

Veeam Backup & Replication provides a centralized console for administering backup, restore and replication operations in all supported platforms (virtual, physical, cloud). Also, the console allows you to automate and schedule routine data protection operations and integrate with solutions for alerting and generating compliance reports.

This section contains an overview of Veeam Backup & Replication and solutions integrated with it.

Main Features

Main functionality of Veeam Backup & Replication includes:

* [Backup](backup.md): creating image-level backups of virtual, physical, cloud machines and backups of file shares and object storage repositories.
* [Restore](data_recovery.md): performing restore from backup files to the original or a new location. Veeam Backup & Replication offers a number of recovery options for various disaster recovery scenarios, including Instant Recovery, image-level restore, file-level restore, restore of application items and so on.

* [Replication](replication.md): creating an exact copy of a VM and maintaining the copy in sync with the original VM.
* [Continuous Data Protection (CDP)](cdp_replication.md): replication technology that helps you protect mission-critical VMs and reach recovery point objective (RPO) up to seconds.
* [Backup Copy](backup_copy.md): copying backup files to a secondary repository.
* [Storage System Snapshot Integration](storage_integration.md): backing up and restoring VMs using capabilities of native snapshots created on storage systems.
* [Tape Devices Support](tape_device_support.md): storing copies of backups in tape devices.
* [Recovery Verification](surebackup_recovery_verification.md): testing VM backups and replicas before recovery.
* [Scale-Out Backup Repositories](backup_repository_sobr.md): a repository system that allows you to distribute data between performance, capacity and archive tiers.

Protected Objects

With Veeam Backup & Replication, you can back up and restore the following objects:

* Virtual machines:

* [VMware vSphere VMs](backup.md)
* [VMware Cloud Director VMs](vcloud_director_backup.md)
* [Microsoft Hyper-V VMs](backup.md)

* [Nutanix AHV VMs](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9)
* [oVirt VMs](https://helpcenter.veeam.com/docs/vbrhv/userguide/overview.html?ver=7)\*
* [Proxmox VE VMs](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/overview.html?ver=3)
* [Scale Computing HyperCore VMs](https://helpcenter.veeam.com/docs/vpsch/userguide/overview.html?ver=2)

* Cloud workloads:

* [AWS EC2 instances](https://helpcenter.veeam.com/docs/vbaws/guide/overview_ec2.html?ver=10)
* [AWS RDS resources](https://helpcenter.veeam.com/docs/vbaws/guide/overview_rds.html?ver=10)
* [AWS DynamoDB tables](https://helpcenter.veeam.com/docs/vbaws/guide/overview_dynamo.html?ver=10)
* [AWS Redshift clusters](https://helpcenter.veeam.com/docs/vbaws/guide/overview_redshift.html?ver=10)
* [AWS Redshift Serverless](https://helpcenter.veeam.com/docs/vbaws/guide/overview_redshift_serverless.html?ver=10)
* [AWS EFS file systems](https://helpcenter.veeam.com/docs/vbaws/guide/overview_efs.html?ver=10)
* [AWS FSx file systems](https://helpcenter.veeam.com/docs/vbaws/guide/overview_fsx.html?ver=10)
* [AWS VPC configurations](https://helpcenter.veeam.com/docs/vbaws/guide/overview_vpc_configurations.html?ver=10)
* [Microsoft Azure VMs](https://helpcenter.veeam.com/docs/vbazure/guide/overview_vm.html?ver=8.1)
* [Microsoft Azure SQL databases](https://helpcenter.veeam.com/docs/vbazure/guide/overview_sql.html?ver=8.1)
* [Microsoft Azure Cosmos DB accounts](https://helpcenter.veeam.com/docs/vbazure/guide/overview_cosmos_db.html?ver=8.1)
* [Microsoft Azure file shares](https://helpcenter.veeam.com/docs/vbazure/guide/overview_fs.html?ver=8.1)
* [Microsoft Azure virtual network configurations](https://helpcenter.veeam.com/docs/vbazure/guide/overview_vnet.html?ver=8.1)
* [Google Cloud VMs](https://helpcenter.veeam.com/docs/vbgc/guide/overview_vm.html?ver=7)\*
* [Google Cloud SQL instances](https://helpcenter.veeam.com/docs/vbgc/guide/overview_sql.html?ver=7)\*
* [Google Cloud Spanner instances](https://helpcenter.veeam.com/docs/vbgc/guide/overview_spanner.html?ver=7)\*

* [Microsoft Entra ID tenant data](https://helpcenter.veeam.com/docs/vbr/entraid/overview.html?ver=13)
* [Unstructured data](unstructured_data_backup.md):

* [File servers](adding_managed_server_file_share.md)
* [File shares](adding_file_share.md)
* [Enterprise NAS systems](adding_nas_filer.md)
* [Object storage repositories](adding_object_storage.md)

* Physical machines. To back up machines running Windows, Linux or macOS operating systems, Veeam Backup & Replication uses backup agents installed on each computer. Veeam Backup & Replication operates as a centralized control center for deploying and managing Veeam Agent for Microsoft Windows, Veeam Agent for Linux, Veeam Agent for Mac, Veeam Agent for Oracle Solaris and Veeam Agent for IBM AIX. For details, see [Veeam Agent Backup](agents_introduction.md).

\* - Available on Microsoft Windows-based backup server.

Protected Applications

Native functionality of Veeam Backup & Replication allows you to [create application-consistent backups](application_aware_processing.md) for:

* Microsoft SQL Server
* PostgreSQL
* Oracle Database

* Active Directory
* Microsoft Exchange
* Microsoft SharePoint

Also, you can install the following additional tools:

* [Veeam Backup for Microsoft 365](https://helpcenter.veeam.com/docs/vbo365/guide/vbo_introduction.html?ver=80): for full protection of Microsoft applications.
* [Veeam Plug-Ins for Enterprise Applications](protect_applications.md): for integration of Veeam Backup & Replication with Oracle RMAN, SAP HANA Backint, and BR\*Tools.

Management and Reporting

Veeam Backup & Replication integrates with a set of solutions that provide reporting and management capabilities for enterprise environments:

* [Veeam ONE](https://helpcenter.veeam.com/docs/one/deployment/about.html?ver=13): a solution that enables real-time monitoring, business documentation and management reporting for Veeam Backup & Replication, VMware vSphere and Microsoft Hyper-V.
* [Veeam Backup Enterprise Manager](https://helpcenter.veeam.com/docs/vbr/em/introduction.html?ver=13): a management and reporting component that allows you to manage multiple Veeam Backup & Replication installations from a single web console.

* [Management Pack for Veeam Backup & Replication](https://helpcenter.veeam.com/docs/mp/backup_guide/key_features_and_licensing.html?ver=9a): a component that integrates Veeam Backup & Replication infrastructure, services and jobs into Microsoft System Center Operations Manager.
* [Veeam Recovery Orchestrator](https://helpcenter.veeam.com/docs/vro/userguide/overview.html?ver=13): a solution that orchestrates disaster recovery processes in VMware vSphere environments, supports one-click recovery for critical applications and sites, and provides features for documentation and testing.
* [Veeam App for Splunk](https://helpcenter.veeam.com/docs/security_plugins_splunk/guide/): a Splunk extension that allows you to monitor the health and security status of your Veeam backup infrastructure.
* [Veeam App for Palo Alto Networks XSOAR](https://helpcenter.veeam.com/docs/security_plugins_xsoar/guide/): a Cortex XSOAR content pack that allows you to monitor various security activities in your Veeam backup infrastructure.
* [Veeam App for Palo Alto Networks XSIAM](https://helpcenter.veeam.com/docs/security_plugins_xsiam/guide/): a Cortex XSIAM content pack that allows you to monitor various security activities in your Veeam backup infrastructure.
* [Veeam App for CrowdStrike Falcon LogScale](https://helpcenter.veeam.com/docs/security_plugins_falcon_logscale/guide/):a CrowdStrike app that allows you to monitor various security activities in your Veeam Data Platform environment.
* [Veeam App for Microsoft Sentinel](https://helpcenter.veeam.com/docs/security_plugins_microsoft_sentinel/guide/): a Microsoft Azure app that allows you to monitor backup jobs and various security activities in your Veeam Data Platform environment.

Service Providers

If you are a service provider, you can use [Veeam Service Provider Console](https://helpcenter.veeam.com/docs/vac/provider_admin/about.html?ver=9) to deliver Veeam-powered Backup-as-a-Service (BaaS) and Disaster Recovery-as-a-Service (DRaaS) services to your customers.

You can also use Veeam Backup & Replication to offer cloud repository as a service and disaster recovery as a service. For details, see [Veeam Cloud Connect](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13).

Page updated 12/30/2025

Page content applies to build 13.0.1.1071
