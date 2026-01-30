---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_permissions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Permissions


For general requirements for permissions that must be provided to the user account to install and work with Veeam Backup & Replication, see [Permissions](required_permissions.md). In addition to general port requirements, for the Veeam Agent management scenarios the following permissions must be provided.

Keep in mind that the list of required permissions differs depending on the functionality that you use. Make sure that user accounts have permissions listed in the following subsections:

* [Permissions for Backup of Cloud Machines](#cloud_m)
* [Permissions for Backup to Object Storage](#obj_stor)
* [Permissions for Guest Processing](#guest)

|  |
| --- |
| NOTE |
| If you plan to back up data using a direct connection between the Veeam Agent computer and object storage, consider the access permissions in [Access Permissions for Direct Connection to Object Storage](agents_object_storage_direct_access.md). |

Permissions for Backup of Cloud Machines

The list of permissions differs depending on the type of the cloud machines you plan to back up:

* [Microsoft Azure virtual machines](#cloud_azure)
* [Amazon EC2 instances](#cloud_amazon)

Microsoft Azure Virtual Machines

If you want to back up Microsoft Azure virtual machines, a Microsoft Azure Compute Account that you use must have the following permissions:

|  |
| --- |
| { |

The permissions are assigned in the following ways:

* If you use an existing Microsoft Azure Compute Account, make sure to assign the required permissions.
* If you create a new Microsoft Azure Compute Account with Veeam Backup & Replication, the required permissions are assigned to the newly created account automatically.

To learn more, see [Microsoft Azure Compute Accounts](restore_azure_accounts.md).

Amazon EC2 Instances

If you want to back up Amazon EC2 instances, make sure the user account that you use has the following permissions:

|  |
| --- |
| {   "ec2:AssociateIamInstanceProfile",   "ec2:DescribeIamInstanceProfileAssociations",   "ec2:DescribeInstances",   "iam:AddRoleToInstanceProfile",   "iam:AttachRolePolicy",   "iam:CreateInstanceProfile",   "iam:CreateRole",   "iam:GetRole",   "iam:GetUser",   "iam:PassRole",   "iam:SimulatePrincipalPolicy",   "sqs:\*",   "ssm:DescribeInstanceInformation",   "ssm:GetCommandInvocation",   "ssm:SendCommand",   "ssm:UpdateManagedInstanceRole" } |

Permissions for Backup to Object Storage

The general permissions for backup to object storage are listed in section [Using Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/required_permissions.html?ver=13#using-object-storage-repositories). Additional permissions are required for object storage in the Veeam Agent management infrastructure. The list of additional permissions differs depending on the selected object storage and the way you set your backup infrastructure:

* [Amazon S3](#aws_s3)
* [S3 compatible (including IBM Cloud Object Storage and Wasabi Cloud Storage)](#s3)
* [Google Cloud Storage](#google)

Amazon S3

Consider the following:

* Make sure the user account you are using has access to Amazon buckets and folders.
* The ListAllMyBuckets permission is not required if you specify the bucket name explicitly at the Bucket step of the New Object Repository wizard.
* If you plan to use Amazon S3 storage with immutability enabled, see permissions required for immutability in section [Using Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/required_permissions.html?ver=13#using-object-storage-repositories). To learn more about immutability, see [Backup Immutability](agents_object_storage_backup_immutability.md).

Make sure that your infrastructure configuration fits the following description:

* You plan to back up data to the Amazon S3 storage.
* You selected direct connection in the object storage settings. To learn more, see [Adding Amazon S3 Object Storage](adding_amazon_object_storage.md).

If you plan to back up data using such infrastructure configuration, make sure the user account that you use to connect to the object storage has the following permissions:

|  |
| --- |
| {   "iam:AttachUserPolicy",   "iam:CreateAccessKey",   "iam:CreatePolicy",   "iam:CreatePolicyVersion",   "iam:CreateUser",   "iam:DeleteAccessKey",   "iam:DeletePolicy",   "iam:DeletePolicyVersion",   "iam:DeleteUser",   "iam:DeleteUserPolicy",   "iam:DetachUserPolicy",   "iam:GetPolicy",   "iam:GetPolicyVersion",   "iam:GetUser",   "iam:GetUserPolicy",   "iam:ListAccessKeys",   "iam:ListAttachedUserPolicies",   "iam:ListPolicyVersions",   "iam:ListUserPolicies",   "iam:PutUserPolicy",   "iam:SetDefaultPolicyVersion",   "iam:SimulatePrincipalPolicy",   "iam:TagUser" } |

S3 Compatible (Including IBM Cloud Object Storage, Wasabi Cloud Storage)

Consider the following:

* Make sure the user account you are using has access to Amazon buckets and folders.
* The ListAllMyBuckets permission is not required if you specify the bucket name explicitly at the Bucket step of the New Object Repository wizard.
* If you plan to use Amazon S3 storage with immutability enabled, see permissions required for immutability in section [Using Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/required_permissions.html?ver=13#using-object-storage-repositories). To learn more about immutability, see [Backup Immutability](agents_object_storage_backup_immutability.md).

Make sure that your infrastructure configuration fits the following description:

* You plan to back up data to the S3 compatible storage.
* Direct connection is selected in the object storage settings. To learn more, see [Specify Object Storage Account](compatible_repository_account.md).

* The Provided by IAM/STS object storage capabilities option is selected for the object storage. To learn more, see [Managing Permissions for S3 Compatible Object Storage](access_permissions.md).

If you plan to back up data using such infrastructure configuration, make sure the user account that you use to connect to the object storage has the following permissions:

|  |
| --- |
| {   "iam:AttachUserPolicy",   "iam:CreateAccessKey",   "iam:CreatePolicy",   "iam:CreatePolicyVersion",   "iam:CreateUser",   "iam:DeleteAccessKey",   "iam:DeletePolicy",   "iam:DeletePolicyVersion",   "iam:DeleteUser",   "iam:DeleteUserPolicy",   "iam:DetachUserPolicy",   "iam:GetPolicy",   "iam:GetPolicyVersion",   "iam:GetUser",   "iam:GetUserPolicy",   "iam:ListAccessKeys",   "iam:ListAttachedUserPolicies",   "iam:ListPolicyVersions",   "iam:ListUserPolicies",   "iam:PutUserPolicy",   "iam:SetDefaultPolicyVersion",   "sts:GetCallerIdentity" } |

Google Cloud Storage

If you plan to use Google Cloud Storage with immutability enabled, see permissions required for immutability in section [Using Object Storage Repositories](https://helpcenter.veeam.com/docs/vbr/userguide/required_permissions.html?ver=13#google-cloud-object-storage-permissions). To learn more about immutability, see [Backup Immutability](agents_object_storage_backup_immutability.md).

Make sure that your infrastructure configuration fits the following description:

* You plan to back up data to the Google Cloud storage.
* You configured Helper Appliance in the object storage settings. To learn more, see [Configuring Helper Appliance](google_cloud_storage_mount_server.md).
* You selected direct connection in the object storage settings. To learn more, see [Specify Object Storage Account](google_cloud_repository_account.md).

If you plan to back up data using such infrastructure configuration, make sure the user account that you specify in the Helper Appliance settings has the following permissions:

|  |
| --- |
| {   "iam.serviceAccounts.create",   "iam.serviceAccounts.delete",   "iam.serviceAccounts.get",   "iam.serviceAccounts.list",   "storage.buckets.get",   "storage.buckets.getIamPolicy",   "storage.buckets.list",   "storage.buckets.setIamPolicy",   "storage.buckets.update",   "storage.hmacKeys.create",   "storage.hmacKeys.delete",   "storage.hmacKeys.get",   "storage.hmacKeys.list",   "storage.objects.create",   "storage.objects.delete",   "storage.objects.get",   "storage.objects.list",   "storage.objects.setRetention",   "storage.objects.update" } |

Permissions for Guest Processing

To use guest processing, make sure to configure user accounts according to the following requirements.

Consider the following general requirements when choosing a user account:

* For Linux computers, choose a user account with root privileges and with the home directory created.
* If you plan to perform file indexing for Microsoft Windows computers, choose a user account that has administrator privileges.
* If you plan to use guest processing over network for Microsoft Windows computers without listed applications, choose a user account that has administrator privileges.
* When using Active Directory accounts, make sure to provide a user account in the DOMAIN\USERNAME format.
* When using local user accounts, make sure to provide a user account in the USERNAME or HOST\USERNAME format.
* To process a Domain Controller server, make sure that you are using a user account that is a member of the DOMAIN\ADMINISTRATORS group.
* To back up a Read-Only Domain controller, a delegated RODC administrator account is sufficient. For more information, see [Microsoft Documentation](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc755310%28v%3Dws.10%29#Anchor_1).

Depending on the application you need to back up, the user must have the permissions listed in the following table:

| Application | Required Permission |
| --- | --- |
| Microsoft SQL Server | To back up Microsoft SQL Server data, the user whose account you plan to use must be:   * Local Administrator on the Veeam Agent computer. * System administrator (has the Sysadmin role) on the target Microsoft SQL Server.   If you need to provide minimal permissions, the user account must be assigned the following roles and permissions:   * SQL Server instance-level role: public and dbcreator. * Database-level roles and roles for the model system database: db\_backupoperator, db\_denydatareader, public; for the master system database — db\_backupoperator, db\_datareader, public;  for the msdb system database — db\_backupoperator, db\_datareader, public, db\_datawriter. * Securables: view any definition, view server state, connect SQL. |
| Microsoft Active Directory | To back up Microsoft Active Directory data, the user account must be a member of the built-in Administrators group. |
| Microsoft Exchange | To back up Microsoft Exchange data, the user account must have the local Administrator permissions in Microsoft Exchange. |
| Oracle | On Microsoft Windows computers  To back up Oracle data on a Microsoft Windows computer, the user account must be configured as follows:   * The user account must be a member of both the Local Administrators group and the ORA\_DBA group (if OS authentication is used). * The user account must be granted SYSDBA privileges. |
| On Linux computers  To back up Oracle data on a Linux computer, the user account must be configured as follows:   * The user account must be granted SYSDBA privileges.  * To back up Oracle database archived logs, the user account must have the primary membership in the Oracle Inventory Group (oinstall) group. To learn how to configure the Oracle Inventory Group, see [Oracle documentation](https://docs.oracle.com/en/database/oracle/oracle-database/19/cwlin/example-of-creating-minimal-users-roles-groups.html#GUID-103186A1-74E0-42A8-AC3D-15AF833DCB40).   Also, consider the following about backup of Oracle data on a Linux computer:   * You can use either the same account that was specified at the Guest Processing step if such an account is a member of the OSDBA and OINSTALL groups, or you can use any other account that has SYSDBA privileges. For more information about specifying a user account, see [Application-Aware Processing](agent_job_guest.md#aap). * To perform guest processing for Oracle databases on Linux servers, make sure that the /tmp directory is mounted with the exec option. Otherwise, you will get a "Permission denied" error. |
| Microsoft SharePoint | To back up Microsoft SharePoint server, the user account must have the Farm Administrator role.  To back up Microsoft SQL databases of the Microsoft SharePoint Server, the user account must have the same privileges as for the [Microsoft SQL Server](#sql). |
| MySQL | To process the MySQL database system, the MySQL user account must have the following privileges:   * SELECT for all tables. This privilege is required to allow Veeam Agent to access table metadata. To learn more, see [MySQL documentation](https://dev.mysql.com/doc/refman/8.0/en/information-schema-introduction.html). * LOCK TABLES. This privilege is required to allow Veeam Agent to process tables based on the MyISAM storage engine. * RELOAD. This privilege is required to allow the MySQL account to perform FLUSH operations. |
| PostgreSQL | To back up PostgreSQL instances, the user account must have the superuser privileges for the PostgreSQL instance. For more information, see [PostgreSQL documentation](https://www.postgresql.org/docs/current/database-roles.html). |


