---
title: "Glossary"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_glossary.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Glossary


This section describes product-specific terms and abbreviations that appear in the User Guide.

A

* application-aware processing — a Veeam technology that enables quiescing applications on EC2 instances and creating a consistent view of application data. See also [Performing EC2 Backup](aws_add_policy_app_aware_processing.md).
* Availability Zone — a separate data center within an AWS Region that provides high availability for AWS resources in this region. See also [Performing Entire Configuration Export](aws_export_entire_vpc_zone_mapping.md).
* AWS account — a container for AWS resources that is used to manage AWS services, to configure IAM permissions and to handle service billing. See also [Worker Deployment Options](aws_worker_options.md).
* AWS KMS key — a cryptographic key that is used to encrypt and decrypt data associated with AWS resources across AWS services. See also [AWS KMS Encryption](aws_encryption_aws_cmks.md).
* AWS Organization — a collection of AWS accounts that is organized in a hierarchical structure. See also [AWS Organizations](aws_organizations.md).
* Veeam Plug-in for AWS — an architecture component that extends the Veeam Backup & Replication functionality to enable integration of backup appliances into the backup infrastructure. See also [Overview](aws_welcome.md).
* AWS Region — a specific physical location where AWS resources are hosted. See also [Overview](aws_welcome.md).
* AWS services — cloud-based tools and AWS resources that are used for cloud computing, storage, networking and security purposes. See also [AWS Services](aws_system_requirements_aws_services.md).
* AWS tag — a label (key-value pair) assigned to AWS resources that is used to organize and manage them. See also [Performing Backup Using Web UI](aws_add_policy_source_settings.md#instances).

B

* backup appliance — a Linux-based EC2 instance that orchestrates backup and restore tasks, communicates with AWS services and stores configuration data. See also [Solution Architecture](aws_backup_appliances.md).
* backup account — an AWS account that is used to perform operations with AWS resources belonging to either the same or any other AWS account. See also [Worker Deployment Options](aws_worker_options.md).

* Backup Appliance Web UI — a client-side component that is used to access and manage backup appliances through a web browser. See also [Worker Instances in Private Environment](aws_worker_instances_in_private.md).

* backup chain — a sequence of backups created by a backup policy. See also [Protecting EC2 Instances](aws_backup_chain.md).
* backup copy — a Veeam Backup & Replication functionality that enables creating copies of backed-up data in different locations, providing additional data protection and disaster recovery options. See also [Creating Backup Copy Jobs](aws_backup_copy.md).
* backup policy — a collection of settings that define the way backup operations are performed: what data to back up, which operations to perform, where to store backups, when to start the backup process, how to retain restore points and so on. See also [Performing EC2 Backup](aws_perform_ec2_backup.md).
* backup repository — a folder in an Amazon S3 bucket where the backup appliance stores backups created by backup polices. See also [Solution Architecture](aws_backup_repositories.md).
* backup server — a physical or virtual machine (Windows-based or Linux-based) that serves as the core component of the backup infrastructure. See also [Solution Architecture](aws_backup_server.md).
* backup vault — an AWS container where the backup appliance stores cloud-native backups created by backup polices. See also [Performing DynamoDB Backup](aws_add_policy_target_settings_backups_dynamo.md).
* Block Generation — a Veeam technology that enables managing immutability periods for backed-up data stored in backup repositories. See also [Immutability](aws_immutability.md).

C

* changed block tracking (CBT) — a Veeam technology that enables tracking data block changes to reduce the amount of data read from processed EBS volumes, and to increase the speed and efficiency of incremental backups. See also [Changed Block Tracking](aws_cbt.md).
* cloud-native backup — a restore point that the backup appliance takes using native AWS capabilities to capture the whole image of a processed AWS resource (DynamoDB table, EFS file system, FSx file system, Redshift cluster or Redshift Serverless namespaces) at a specific point of time. See also [Protecting DynamoDB Tables](aws_overview_dynamo.md).
* cloud-native snapshot — a restore point that the backup appliance takes using native AWS capabilities to capture either a set of point-in-time snapshots created for EBS volumes of an EC2 instance or a storage volume snapshot created for an RDS resource (DB instance or Amazon Aurora DB cluster). See also [Protecting EC2 Instances](aws_overview_ec2.md).
* configuration database — a backup appliance component that stores data on backup policies, sessions, worker instance configurations, IAM roles, AWS resources and so on. See also [Performing Configuration Backup Using Web UI](aws_config_backup_ui.md).
* Cloud Credentials Manager — a configuration database where Veeam Backup & Replication stores credential records that are used to connect to components of the backup infrastructure (such as servers, virtual machines and cloud services). See also [Deploying Backup Appliance](aws_deploying_appliances.md).

D

* database account — credentials that are used to access databases of PostgreSQL DB instances when performing image-level backup and restore operations. See also [Managing Database Accounts](aws_accounts_database.md).
* Default Backup Restore role — a role that is automatically added to the backup appliance after its deployment and used to perform data protection and recovery operations within the AWS account to which the backup appliance belongs. See also [Deploying Backup Appliance](aws_deploying_appliances.md).

G

* gateway server — an auxiliary backup infrastructure component that provides access from the backup server to the repositories. See also [Connecting to Existing Appliances](aws_connect_appliance_repo.md#gateway).
* guest scripting — a backup appliance functionality that enables running custom scripts on EC2 instances before and after backup operations. See also [Performing EC2 Backup](aws_add_policy_guest_processing.md).

H

* health check — a backup appliance functionality that enables verifying the availability of data blocks in backup files and cyclic redundancy check (CRC) values of metadata to ensure its integrity. See also [Performing EC2 Backup](aws_add_policy_retry_notification.md).

I

* IAM permissions — specific actions that are granted to IAM roles to allow access to AWS services and resources. See also [IAM Permissions](aws_system_requirements_permissions.md).
* IAM policy — an AWS object that is attached to IAM roles to define their permissions. See also [Appendix B. Creating IAM Policies in AWS](aws_create_iam_policy.md).
* IAM role — an IAM identity whose permissions the backup appliance uses to access AWS services and resources. See also [Appendix A. Creating IAM Roles in AWS](aws_create_iam_policy_role.md).
* IAM user — an IAM identity whose permissions the backup appliance uses to perform restore operations. See also [Plug-In Permissions](aws_req_permissions.md#aws_account).
* image-level backup — a restore point that captures the whole image of the processed AWS resource (including OS data, application data and so on) at a specific point in time. See also [EC2 Backup](aws_backup_chain.md).
* Impersonation IAM role — a specific IAM role created on the backup appliance after its deployment and used to assume IAM roles added to the backup appliance to perform operations in the backup infrastructure. See also [Managing IAM Roles](aws_byb_roles.md).
* immutability — a backup appliance functionality that enables protecting restore points stored in backup repositories from deletion or loss as a result of malware, ransomware or any other malicious actions. See also [Immutability](aws_immutability.md).

M

* mount server — an auxiliary backup infrastructure component that provides access between the backup server and repositories added to the backup infrastructure. See also [Managing Backup Repositories](aws_add_s3_mount_server.md).

N

* namespace — a collection of database objects and users in Amazon Redshift Serverless. See also [Protecting Redshift Serverless](aws_overview_redshift_serverless.md).

O

* organizational unit — a logical subdivision within AWS Organizations that is used to group and manage AWS accounts. See also [AWS Organizations](aws_organizations.md).

P

* parameter group — a set of settings containing database engine configuration values applied to RDS resources. See also [RDS Restore Using Web UI](aws_restore_rds_instance_settings.md).
* product updates — updates for the backup appliance components that deliver new features and improvements. See also [Upgrading Backup Appliances](aws_upgrade_appliance_console.md).
* production account — an AWS account in which the backup appliance deploys worker instances to perform operations with processed AWS resources belonging to the same AWS account. See also [Worker Deployment Options](aws_worker_options.md#production).

R

* restore point — a point-in-time cloud-native snapshot, snapshot replica, cloud-native backup and image-level backup that can be used to restore an AWS resource. See also [Snapshot Chain](aws_snapshot_chain.md).
* retention policy — a collection of settings that define how long the backup appliance keeps restore points produced by backup policies. See also [Retention Policies](aws_backup_retention.md).

S

* security group — a virtual firewall that controls inbound and outbound traffic for AWS resources. See also [RDS Backup](aws_backup_hiw_rds.md).
* Self Backup service — a service that enables backing up and restoring the configuration database of the backup appliance. See also [Performing Configuration Backup and Restore](aws_config_backup.md).
* schedule-based backup policy — a collection of settings that define the way backup operations are performed: what data to back up, which operations to perform, where to store backups, when to start the backup process, how to retain restore points, and so on. See also [Protecting EC2 Instances](aws_overview_ec2.md).
* SLA-based backup policy — a collection of settings that automate the way backup operations are performed: what data to back up, how frequently to run the backup process, what region-specific repositories to use to store backups, how many restore points should be created in time to meet SLA requirements, and so on. See also [Protecting EC2 Instances](aws_overview_ec2.md).
* software package updates — updates for the backup appliance software components such as .NET, PostgreSQL, and other third-party packages required for proper operation. See also [Upgrade and Update](aws_update_vb.md).
* subnet group — a collection of subnets within Amazon VPC networks assigned to AWS services for deploying and managing AWS resources. See also [RDS Restore Using Web UI](aws_restore_rds_network.md).

T

* tape device — a hardware component that records and reads data sequentially, commonly used for long-term backup archiving. See also [Additional Repositories and Tape Devices](aws_additional_repos_and_tape_devices.md).

V

* Veeam Plug-in for AWS REST API service — a service that allows users to perform operations with the backup appliance entities using HTTP requests and standard HTTP methods. See also [Ports](aws_ports.md).

* Veeam Backup & Replication console — a client-side component that provides access to the backup server. See also [Overview](aws_welcome.md).
* Veeam Data Mover — a service that is responsible for data processing and transfer. It optimizes backup performance by compressing, encrypting and transporting data between source and target locations. See also [Solution Architecture](aws_backup_repositories.md).
* Veeam FLR service — a service that enables restoring individual files and folders of protected EC2 instances. See also [Performing File-Level Recovery](aws_restore_item_perform.md).
* Veeam Updater service — a service that enables checking, viewing and installing product and software package updates. See also [Installing Updates](aws_updates_install.md).

* VPC interface endpoint — a private connection within an Amazon VPC network created using AWS PrivateLink to enable access to AWS services. See also [Worker Instances in Private Environment](aws_worker_instances_in_private.md).

W

* worker configuration — a group of network settings that the backup appliance uses to deploy worker instances in a specific AWS Region to perform data protection and disaster recovery operations. See also [Managing Worker Configurations](aws_worker_settings.md).
* worker profile — a type of worker instance that the backup appliance deploys in a specific AWS Region to perform data protection and disaster recovery operations. See also [Managing Worker Profiles](aws_worker_profiles.md).
* worker instance — a temporary Linux-based EC2 instance that is responsible for the interaction between the backup appliance, AWS services and other backup appliance components. See also [Worker Instances](aws_worker_instances.md).
* workgroup — a collection of compute resources in Amazon Redshift Serverless. See also [Protecting Redshift Serverless](aws_overview_redshift_serverless.md).
* workload — any AWS resource (for example, an EC2 instance, a RDS resource, a DynamoDB table and so on) that can be protected by Veeam Plug-in for AWS. See also [Managing Backed-Up Data](aws_managing_data_console.md).

Page updated 2026-06-02

