---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/required_permissions.html"
last_updated: "12/29/2025"
product_version: "13.0.1.1071"
---

# Permissions


Make sure the user accounts that you plan to use have permissions described in the following sections.

Installing and Using Veeam Backup & Replication

The accounts used for installing and using Veeam Backup & Replication must have the following permissions.

| Account | Required Permission |
| --- | --- |
| Installation for Veeam Backup & Replication on Microsoft Windows | The account used to install the product must have the local Administrator permissions on the target machine. |
| Installation for Veeam Backup & Replication on Linux from .ISO | The account used to install the product must have access to manage input/output and boot devices. If you install Veeam Backup & Replication on a VM, the account must also have permission to create virtual machines with attached disk images on the hypervisor level. |
| Installation for Veeam Backup & Replication on Linux from .OVA | The account used to install the product must have permissions to deploy .OVA files. For details on the minimum required permissions, see the [Permissions Reference](https://helpcenter.veeam.com/docs/vbr/permissions/installation.html?ver=13). |
| Veeam Backup & Replication Console Permissions | The account used to install the Veeam Backup & Replication console must have the local Administrator permissions on the machine where the console will be installed. After installation, users can have standard (non-administrative) privileges to connect to the console.  When connecting to backup server, the console automatically checks for updates. If the backup server has been updated (for example, after installing a private fix or upgrading to a new product version), or if any console program files or services are missing, the console prompts users to elevate their rights to administrator to complete the update process. After the update, users can connect to and use the console with standard user privileges.  [For recovery of Microsoft Windows VM guest OS files] If you plan to [save files to a new location](guest_restore_save.md#other), the user who launched the Veeam Backup & Replication console does not have permissions to read and write data to the new location, and the mount point is located on the same machine as the Veeam Backup & Replication console, check that the user has the SeBackupPrivilege and SeRestorePrivilege. For more information on where mount points are created, see [Mount Points and Restore Scenarios](guest_restore_scenarios.md).  Accounts that are members of the Protected Users Active Directory group cannot be used to access the backup server remotely over the Veeam Backup & Replication console. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/windows-server/security/credentials-protection-and-management/protected-users-security-group). |
| [Veeam Backup & Replication Services](services_and_components.md) for Veeam Backup & Replication on Microsoft Windows | The account used to run the Veeam Backup & Replication Services must be the LocalSystem account or must have local Administrator permissions on the backup server.  These privileges are required because the services need access to the Veeam registry configuration, which is available only to privileged users. Some services also perform disk management operations, open ports in firewalls and perform other operations that require a high permission level. |
| Microsoft SQL Server | You require different sets of Microsoft SQL permissions in the following cases:   * Installation (remote or local): current account needs CREATE ANY DATABASE permission on the SQL server level. After database creation this account automatically gets a db\_owner role and can perform all operations with the database. If the current account does not have this permission, a Database Administrator may create an empty database in advance and grant the db\_owner role to the account that will be used for installing Veeam Backup & Replication. * Upgrade: current account should have sufficient permissions for that database. To grant these permissions through role assignment, it is recommended that you use the account with db\_owner role. * Operation: the account used to run Veeam Backup Service requires db\_datareader and db\_datawriter roles as well as permissions to execute stored procedures for the configuration database on the Microsoft SQL Server. Alternatively, you can assign db\_owner role for this database to the service account.   For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles?view=sql-server-ver15). |
| PostgreSQL | The account used for installation, upgrade and operation requires superuser role. |

Using Virtualization Servers and Hosts

The following permissions and roles are required to work with virtualization servers and hosts during data protection tasks.

| Component | Required Permission or Role |
| --- | --- |
| Source/Target VMware vSphere Host | Root permissions on the ESXi host. When adding the credentials, use the MACHINE\USER format for local accounts or DOMAIN\USER format for domain accounts.  If the vCenter Server is added to the backup infrastructure, an account that has administrative permissions is required. You can either grant the Administrator role to the account or configure granular vCenter Server permissions for certain Veeam Backup & Replication operations in the VMware vSphere environment. For more information, see the [Permissions Reference](https://helpcenter.veeam.com/docs/vbr/permissions/installation.html?ver=13). |
| VMware Cloud Director Server | The account that you specify when adding a server must have system administrator privileges on VMware Cloud Director. You cannot use the organization administrator account to add the Cloud Director server. |
| Source / Target Hyper-V host or cluster | Administrator permissions. |
| SCVMM | Any SCVMM user. This user must have administrator permissions on the Hyper-V hosts and clusters managed by SCVMM and involved in the data protection operations. |
| Windows Server [added to the backup infrastructure](add_windows_server.md) | User account must be in the local administrators group (on the server being added). When adding the credentials, use the MACHINE\USER format for local accounts or DOMAIN\USER format for domain accounts. |
| Linux Server [added to the backup infrastructure](add_linux_server.md) | Root or equivalent permissions. |
| SMB Backup Repository | Read and write permission on the target folder and share. |
| Dell Data Domain Deduplicating Storage Appliance | Access permissions on the DD Boost storage unit where backup data will be kept. To specify the DD Boost User account settings, in Data Domain System Manager, open the Data Management > DD Boost Settings tab. |
| HPE StoreOnce Deduplicating Storage Appliance | Access permissions on the Catalyst store where backup data will be kept. To check the client account permissions, in the HPE StoreOnce management console, select the Catalyst store and open the Permissions tab for it. |

Performing Guest Processing

To use guest OS processing (application-aware processing, pre-freeze and post-thaw scripts, transaction log processing, guest file indexing and file exclusions), make sure to configure your accounts according to the requirements listed in this section. For more information on guest processing, see [Guest Processing](guest_processing.md).

All user accounts used for guest processing of Windows VMs must have the following permissions:

* Logon as a batch job granted
* Deny logon as a batch job not set

Group Managed Service Accounts (gMSAs) must also have the following permissions:

* Logon as a service granted.
* Deny logon as a service not set.

Other permissions depend on applications that you back up. You can find permissions for backup operations in the following table. For restore operation permissions, see Permissions sections in the [Veeam Explorers User Guide](https://helpcenter.veeam.com/docs/vbr/explorers/explorers_introduction.html?ver=13).

| Application | Required Permission |
| --- | --- |
| Microsoft SQL Server | To back up Microsoft SQL Server data, the user whose account you plan to use must be:   * Local Administrator on the target VM. * System administrator (has the Sysadmin role) on the target Microsoft SQL Server.   If you need to provide minimal permissions, the account must be assigned the following roles and permissions:   * SQL Server instance-level role: public and dbcreator. * Database-level roles and roles for the model system database: db\_backupoperator, db\_denydatareader, public; for the master system database — db\_backupoperator, db\_datareader, public;  for the msdb system database — db\_backupoperator, db\_datareader, public, db\_datawriter. * Securables: view any definition, view server state, connect SQL. |
| Microsoft Active Directory | To back up Microsoft Active Directory data, the account must be a member of the built-in Administrators group. |
| Microsoft Exchange | To back up Microsoft Exchange data, the account must have the local Administrator permissions on the machine where Microsoft Exchange is installed. |
| Oracle | The account specified at the Guest Processing step must be configured in the following way:   * For a Windows-based VM, the account must be a member of both the Local Administrator group and the ORA\_DBA group (if OS authentication is used). In addition, if ASM is used, then such an account must be a member of the ORA\_ASMADMIN group (for Oracle 12 and higher). * For a Linux-based VM, the account must be a Linux user elevated to root. The account must have the home directory created.   To back up Oracle databases, you can specify the following options at the [Oracle](backup_job_vss_oracle_vm.md) tab:   * Oracle account with SYSDBA privileges.   You can use, for example, the SYS Oracle account or any other Oracle account that has been granted SYSDBA privileges.   * Account specified for guest processing. That is, the Use guest credentials option selected.   In this case, the account that was specified at the Guest Processing step must be a member of the ORA\_DBA group for a Windows-based VM and OSASM, OSDBA and OINSTALL groups for a Linux-based VM.  To perform guest processing for Oracle databases on Linux servers, make sure that the /tmp directory is mounted with the exec option. Otherwise, you will get an error with the permission denial. |
| Microsoft SharePoint | To back up a Microsoft SharePoint Server, the account must have the Farm Administrator role.  To back up Microsoft SQL databases of the Microsoft SharePoint Server, the account must have permissions required for [Microsoft SQL Server](#vesql) backup operations. |
| PostgreSQL | The account specified at the Guest Processing step must be a Linux user elevated to root. The account must have the home directory created.  For the directory specified as the temporary location for archive logs, the following permissions must be granted:   * The user running the PostgreSQL instance must have read, write, and execute (rwx) permissions. * The user selected in the backup job settings must have read and execute (rx) permissions.   For more information, see [PostgreSQL WAL Files Settings](backup_job_vss_postgresql_vm.md) for VMware vSphere or [PostgreSQL WAL Files Settings](backup_job_vss_postgresql_hv.md) for Microsoft Hyper-V.  To back up PostgreSQL instances, the account must have the superuser privileges for the PostgreSQL instance. For more information, see [PostgreSQL documentation](https://www.postgresql.org/docs/current/database-roles.html).  Note: If you back up data using vSphere API, the account specified at the Guest Processing step must be a root Linux user. |

Consider the following general requirements when choosing a user account:

* [For guest OS file indexing] For Windows-based workloads, choose an account that has administrator privileges. For Linux-based workloads, choose an account of a root user or user elevated to root.

* To use networkless guest processing over VMware VIX/vSphere Web Services (vSphere) or PowerShell Direct (Hyper-V), you must specify one of the following accounts at the Guest Processing step of the backup wizard. Check that the account also has permissions listed in the table.

* If Windows User Account Control (UAC) is enabled, specify Local Administrator (MACHINE\Administrator) or Domain Administrator (DOMAIN\Administrator) account.
* If UAC is disabled, specify an account that is a member of the built-in Administrators group.
* [For vSphere] For Linux-based VMs, specify a root account.

* [For networkless guest processing over VMware VIX] To be able to perform more than 1000 guest processing operations, the user that you specify for guest processing must be logged into the VM at least once.
* [If you plan to use guest processing over network for workloads without listed applications] For Windows-based workloads, choose an account that has administrator privileges. For Linux-based workloads, choose an account of a root user or user elevated to root.
* When using Active Directory accounts, make sure to provide an account in the DOMAIN\Username format.
* When using local user accounts, make sure to provide an account in the Username or HOST\Username format.
* To process a Domain Controller server, make sure that you are using an account that is a member of the DOMAIN\Administrators group.
* To back up a Read-Only Domain controller, a delegated RODC administrator account is sufficient. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc755310%28v%3Dws.10%29#Anchor_1).

Restoring to Amazon EC2

To [restore workloads to Amazon EC2](restore_amazon.md), it is recommended that the IAM user whose credentials you plan to use to connect to AWS has administrative permissions — access to all AWS actions and resources.

If you do not want to provide full access to AWS, you can grant to the IAM user a minimal set of permissions that will be sufficient for restore. For more information, see [AWS IAM User Permissions](restore_amazon_permissions.md).

Restoring to Google Cloud

To [restore workloads to Google Cloud](restore_google.md), the IAM user and the service account must have permissions described in [Google Compute Engine IAM User Permissions](gcp_iam_permissions.md).

Adding Microsoft Azure Compute Accounts

Microsoft Azure Compute account is required to restore workloads to Microsoft Azure, add Azure archive storage and so on. For more information, see [Microsoft Azure Compute Accounts](restore_azure_accounts.md).

The following permissions are required for adding a Microsoft Azure Compute account.

| Microsoft Entra ID (formerly Azure Active Directory) Application | Permissions |
| --- | --- |
| New (select the Create a new account option at the [Subscription](restore_azure_acc_account.md) step of the wizard) | The Microsoft Entra ID user account where the application will be created must have the following privileges:   * To register applications. For this, you can assign the Global Administrator privileges to the user or enable the Users can register applications option for the user in Azure portal. For details, see [Microsoft Azure Docs](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-how-applications-are-added). * To assign a role on the subscription level for the registered application. For this, you can use the Owner\* role or if the Owner role cannot be used, you can create a custom role with minimal permissions. To learn how to create a custom role, see [Creating Custom Role for Azure and Azure Stack Hub Accounts](azure_custom_role.md#hub_new).   \* - When you assign a privileged role, like Owner, using the Azure Portal, the default conditions can be added to this role assignment. With these default conditions, adding the Compute account will fail. To avoid this issue, select the Allow user to assign all roles (highly privileged) option. For more information on conditions, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal#delegate-condition). |
| Existing (select the Use the existing account option at the [Subscription](restore_azure_acc_account.md) step of the wizard) | The application must have the Contributor role privilege for the selected subscription. If you restore workloads to Microsoft Azure Stack Hub and cannot use the Contributor role, you can create a custom role with minimal permissions. To learn how to create a custom role, see [Creating Custom Role for Azure and Azure Stack Hub Accounts](azure_custom_role.md#hub_ex). |

Adding Microsoft Azure Storage Accounts (Entra ID)

Microsoft Azure storage account with Microsoft Entra ID authorization is required to add Azure Blob storage, Azure archive storage, and so on. For more information, see [Microsoft Azure Storage Accounts (Entra ID)](azure_entra_id.md).

The following permissions are required to existing Microsoft Azure storage account with Microsoft Entra ID authorization:

* If you use a new Microsoft Entra ID (formerly Azure Active Directory) application (select the Create a new account option at the [Subscription](restore_azure_acc_account.md) step of the wizard) when adding a Microsoft Azure Stack Hub Compute account, the Microsoft Entra ID user account where the Microsoft Entra ID application will be created must have the following privileges:

1. To register applications. For this, you can assign the Global Administrator privileges to the user or enable the Users can register applications option for the user in Azure portal. For details, see [Microsoft Azure Docs](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-how-applications-are-added).

1. To assign a role on the subscription level for the registered application. For this, you can use the Owner role or if the Owner role cannot be used, you can create a custom role with minimal permissions. To learn how to create a custom role, see [Creating Custom Role for Azure and Azure Stack Hub Accounts](azure_custom_role.md#hub_new).

* If you use an existing Microsoft Entra ID (formerly Azure Active Directory) application (select the Use the existing account option at the [Account Type](entraid_access.md) step of the wizard), the application must have the following role privileges for the selected storage account:

* Storage Account Contributor
* Storage Blob Data Contributor
* Storage Blob Data Owner

For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles).

Using Object Storage Repositories

General Amazon S3 and S3 Compatible Object Storage Permissions

Consider the following:

* Make sure the account you are using has access to Amazon buckets and folders.
* The ListAllMyBuckets permission is not required if you specify the bucket name explicitly at the Bucket step of the [New Object Repository](adding_amazon_object_storage.md) wizard.

Permissions for Amazon S3 or S3 compatible object storage depend on whether you use [immutability](immutability_sobr.md) and [helper appliance](amazon_storage_mount_server.md#helper) settings.

|  |
| --- |
| Note |
| Consider the following:   * S3 compatible object storage repositories use the same permissions as Amazon S3 object storage with the following exception: since you cannot setup helper appliance in the cloud, you do not need permissions for it. Therefore, S3 compatible object storage repositories require permissions which start with s3, for example, "s3:ListBucket". Permissions that start with ec2 can be skipped, for example, "ec2:DescribeInstances". * To deploy S3 compatible object storage in multiple bucket mode, you must add the s3:CreateBucket and s3:DeleteBucket permissions to the list of permissions that you are going to use. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)1. Immutability Disabled and Helper Appliance not Used

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability disabled. A helper appliance is not used for health check operations.  |  | | --- | | {      "Version": "2012-10-17",      "Statement": [          {              "Effect": "Allow",              "Action": [                "s3:ListBucket",                "s3:GetBucketLocation",                "s3:GetObject",                "s3:PutObject",                "s3:DeleteObject",                "s3:ListAllMyBuckets",                "s3:GetBucketVersioning",               "s3:GetBucketObjectLockConfiguration"              ],              "Resource": "\*"          }      ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)2. Immutability Disabled and New Helper Appliance Configured

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability disabled. For health check operations a new helper appliance is configured and the Amazon VPC, subnet and security group settings are set to (Create new) for the [helper appliance settings](amazon_storage_mount_server.md#helper).  |  | | --- | | {     "Version": "2012-10-17",     "Statement": [     {         "Effect": "Allow",         "Action": [         "s3:ListBucket",         "s3:GetBucketLocation",         "s3:GetObject",         "s3:PutObject",         "s3:DeleteObject",         "s3:ListAllMyBuckets",         "s3:GetBucketVersioning",         "s3:GetBucketObjectLockConfiguration",         "ec2:DescribeInstances",         "ec2:CreateKeyPair",         "ec2:DescribeKeyPairs",         "ec2:RunInstances",         "ec2:DeleteKeyPair",         "ec2:DescribeVpcAttribute",         "ec2:CreateTags",         "ec2:DescribeSubnets",         "ec2:TerminateInstances",         "ec2:DescribeSecurityGroups",         "ec2:DescribeImages",         "ec2:DescribeVpcs",         "ec2:CreateVpc",         "ec2:CreateSubnet",         "ec2:DescribeAvailabilityZones",         "ec2:CreateRoute",         "ec2:CreateInternetGateway",         "ec2:AttachInternetGateway",         "ec2:ModifyVpcAttribute",         "ec2:CreateSecurityGroup",         "ec2:DeleteSecurityGroup",         "ec2:AuthorizeSecurityGroupIngress",         "ec2:AuthorizeSecurityGroupEgress",         "ec2:DescribeRouteTables",         "ec2:DescribeInstanceTypes"             ],         "Resource": "\*"         }     ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)3. Immutability Disabled and Helper Appliance Configured Beforehand

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability disabled. Amazon VPC, subnet and security group settings for a helper appliance are configured beforehand.  |  | | --- | | {     "Version": "2012-10-17",     "Statement": [     {         "Effect": "Allow",         "Action": [         "s3:ListBucket",         "s3:GetBucketLocation",         "s3:GetObject",         "s3:PutObject",         "s3:DeleteObject",         "s3:ListAllMyBuckets",         "s3:GetBucketVersioning",         "s3:GetBucketObjectLockConfiguration",         "ec2:DescribeInstances",         "ec2:CreateKeyPair",         "ec2:DescribeKeyPairs",         "ec2:RunInstances",         "ec2:DeleteKeyPair",         "ec2:DescribeVpcAttribute",         "ec2:CreateTags",         "ec2:DescribeSubnets",         "ec2:TerminateInstances",         "ec2:DescribeSecurityGroups",         "ec2:DescribeImages",         "ec2:DescribeVpcs"             ],         "Resource": "\*"         }     ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)4. Immutability Enabled and Helper Appliance not Used

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability enabled. A helper appliance is not used for health check operations.  |  | | --- | | {      "Version": "2012-10-17",      "Statement": [          {              "Effect": "Allow",              "Action": [                  "s3:ListBucket",                  "s3:GetBucketLocation",                  "s3:GetObject",                  "s3:PutObject",                  "s3:DeleteObject",                  "s3:ListAllMyBuckets",                  "s3:GetBucketVersioning",                  "s3:GetBucketObjectLockConfiguration",                  "s3:ListBucketVersions",                  "s3:GetObjectVersion",                  "s3:GetObjectRetention",                  "s3:GetObjectLegalHold",                  "s3:PutObjectRetention",                  "s3:PutObjectLegalHold",                  "s3:DeleteObjectVersion"                      ],              "Resource": "\*"          }      ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)5. Immutability Enabled and New Helper Appliance Configured

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability enabled. For health check operations a new helper appliance is configured and the Amazon VPC, subnet and security group settings are set to (Create new) for the [helper appliance settings](amazon_storage_mount_server.md#helper).  |  | | --- | | {     "Version": "2012-10-17",     "Statement": [     {         "Effect": "Allow",         "Action": [         "s3:ListBucket",         "s3:GetBucketLocation",         "s3:GetObject",         "s3:PutObject",         "s3:DeleteObject",         "s3:ListAllMyBuckets",         "s3:GetBucketVersioning",         "s3:GetBucketObjectLockConfiguration",         "s3:ListBucketVersions",         "s3:GetObjectVersion",         "s3:GetObjectRetention",         "s3:GetObjectLegalHold",         "s3:PutObjectRetention",         "s3:PutObjectLegalHold",         "s3:DeleteObjectVersion",         "ec2:DescribeInstances",         "ec2:CreateKeyPair",         "ec2:DescribeKeyPairs",         "ec2:RunInstances",         "ec2:DeleteKeyPair",         "ec2:DescribeVpcAttribute",         "ec2:CreateTags",         "ec2:DescribeSubnets",         "ec2:TerminateInstances",         "ec2:DescribeSecurityGroups",         "ec2:DescribeImages",         "ec2:DescribeVpcs",         "ec2:CreateVpc",         "ec2:CreateSubnet",         "ec2:DescribeAvailabilityZones",         "ec2:CreateRoute",         "ec2:CreateInternetGateway",         "ec2:AttachInternetGateway",         "ec2:ModifyVpcAttribute",         "ec2:CreateSecurityGroup",         "ec2:DeleteSecurityGroup",         "ec2:AuthorizeSecurityGroupIngress",         "ec2:AuthorizeSecurityGroupEgress",         "ec2:DescribeRouteTables",         "ec2:DescribeInstanceTypes"             ],         "Resource": "\*"         }     ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)6. Immutability Enabled and Helper Appliance Configured Beforehand

|  |  |
| --- | --- |
| The following permissions are required to use Amazon S3 or S3 compatible object storage with immutability enabled. Amazon VPC, subnet and security group settings for a helper appliance are configured beforehand.  |  | | --- | | {     "Version": "2012-10-17",     "Statement": [     {         "Effect": "Allow",         "Action": [         "s3:ListBucket",         "s3:GetBucketLocation",         "s3:GetObject",         "s3:PutObject",         "s3:DeleteObject",         "s3:ListAllMyBuckets",         "s3:GetBucketVersioning",         "s3:GetBucketObjectLockConfiguration",         "s3:ListBucketVersions",         "s3:GetObjectVersion",         "s3:GetObjectRetention",         "s3:GetObjectLegalHold",         "s3:PutObjectRetention",         "s3:PutObjectLegalHold",         "s3:DeleteObjectVersion",         "ec2:DescribeInstances",         "ec2:CreateKeyPair",         "ec2:DescribeKeyPairs",         "ec2:RunInstances",         "ec2:DeleteKeyPair",         "ec2:DescribeVpcAttribute",         "ec2:CreateTags",         "ec2:DescribeSubnets",         "ec2:TerminateInstances",         "ec2:DescribeSecurityGroups",         "ec2:DescribeImages",         "ec2:DescribeVpcs"             ],         "Resource": "\*"         }     ]  } | |

For more information on permissions, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/dev/using-with-s3-actions.html).

Amazon S3 Glacier and S3 Compatible with Data Archiving Object Storage Permissions

Permissions for Amazon S3 Glacier and S3 Compatible with data archiving depend on whether you use [immutability](immutability_sobr.md) and the [archiver appliance](glacier_archiver_appliance.md) settings:

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)1. Immutability Disabled and Archiver Appliance not Configured

|  |  |
| --- | --- |
| The following permissions are required for Amazon S3 Glacier and S3 Compatible with data archiving object storage with immutability disabled. VPC, subnet and security group settings are set to (Create new) for the [archiver appliance](glacier_archiver_appliance.md) settings.  |  | | --- | | {   "Version": "2012-10-17",   "Statement": [     {       "Sid": "VisualEditor0",       "Effect": "Allow",       "Action": [         "s3:DeleteObject",         "s3:PutObject",         "s3:GetObject",         "s3:RestoreObject",         "s3:ListBucket",         "s3:AbortMultipartUpload",         "s3:GetBucketVersioning",         "s3:ListAllMyBuckets",         "s3:GetBucketLocation",         "s3:GetBucketObjectLockConfiguration",         "ec2:DescribeInstances",         "ec2:CreateKeyPair",         "ec2:DescribeKeyPairs",         "ec2:RunInstances",         "ec2:DeleteKeyPair",         "ec2:DescribeVpcAttribute",         "ec2:CreateTags",         "ec2:DescribeSubnets",         "ec2:TerminateInstances",         "ec2:DescribeSecurityGroups",         "ec2:DescribeImages",         "ec2:DescribeVpcs",         "ec2:CreateVpc",         "ec2:CreateSubnet",         "ec2:DescribeAvailabilityZones",         "ec2:CreateRoute",         "ec2:CreateInternetGateway",         "ec2:AttachInternetGateway",         "ec2:ModifyVpcAttribute",         "ec2:CreateSecurityGroup",         "ec2:DeleteSecurityGroup",         "ec2:AuthorizeSecurityGroupIngress",         "ec2:AuthorizeSecurityGroupEgress",         "ec2:DescribeRouteTables",         "ec2:DescribeInstanceTypes"       ],       "Resource": "\*"     }   ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)2. Immutability Disabled and Archiver Appliance Configured Beforehand

|  |  |
| --- | --- |
| These permissions apply for Amazon S3 Glacier and S3 Compatible with data archiving object storage with immutability disabled. Amazon VPC, subnet and security group settings for an archiver appliance are configured beforehand.  |  | | --- | | {   "Version": "2012-10-17",   "Statement": [     {       "Sid": "VisualEditor0",       "Effect": "Allow",       "Action": [         "s3:DeleteObject",         "s3:PutObject",         "s3:GetObject",         "s3:RestoreObject",         "s3:ListBucket",         "s3:AbortMultipartUpload",         "s3:GetBucketVersioning",         "s3:ListAllMyBuckets",         "s3:GetBucketLocation",         "s3:GetBucketObjectLockConfiguration",         "ec2:DescribeInstances",         "ec2:CreateKeyPair",         "ec2:DescribeKeyPairs",         "ec2:RunInstances",         "ec2:DeleteKeyPair",         "ec2:DescribeVpcAttribute",         "ec2:CreateTags",         "ec2:DescribeSubnets",         "ec2:TerminateInstances",         "ec2:DescribeSecurityGroups",         "ec2:DescribeImages",         "ec2:DescribeVpcs"       ],       "Resource": "\*"     }   ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)3. Immutability Enabled and Archiver Appliance not Configured

|  |  |
| --- | --- |
| The following permissions are required for Amazon S3 Glacier and S3 Compatible with data archiving object storage with immutability enabled. VPC, subnet and security group settings are set to (Create new) for the [archiver appliance](glacier_archiver_appliance.md) settings.  |  | | --- | | {   "Version": "2012-10-17",   "Statement": [     {       "Sid": "VisualEditor0",       "Effect": "Allow",       "Action": [         "s3:DeleteObject",         "s3:PutObject",         "s3:GetObject",         "s3:RestoreObject",         "s3:ListBucket",         "s3:AbortMultipartUpload",         "s3:GetBucketVersioning",         "s3:ListAllMyBuckets",         "s3:GetBucketLocation",         "s3:GetBucketObjectLockConfiguration",         "s3:PutObjectRetention",         "s3:GetObjectVersion",         "s3:PutObjectLegalHold",         "s3:GetObjectRetention",         "s3:DeleteObjectVersion",         "s3:ListBucketVersions",         "ec2:DescribeInstances",         "ec2:CreateKeyPair",         "ec2:DescribeKeyPairs",         "ec2:RunInstances",         "ec2:DeleteKeyPair",         "ec2:DescribeVpcAttribute",         "ec2:CreateTags",         "ec2:DescribeSubnets",         "ec2:TerminateInstances",         "ec2:DescribeSecurityGroups",         "ec2:DescribeImages",         "ec2:DescribeVpcs",         "ec2:CreateVpc",         "ec2:CreateSubnet",         "ec2:DescribeAvailabilityZones",         "ec2:CreateRoute",         "ec2:CreateInternetGateway",         "ec2:AttachInternetGateway",         "ec2:ModifyVpcAttribute",         "ec2:CreateSecurityGroup",         "ec2:DeleteSecurityGroup",         "ec2:AuthorizeSecurityGroupIngress",         "ec2:AuthorizeSecurityGroupEgress",         "ec2:DescribeRouteTables",         "ec2:DescribeInstanceTypes"       ],       "Resource": "\*"     }   ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)4. Immutability Enabled and Archiver Appliance Configured Beforehand

|  |  |
| --- | --- |
| These permissions apply for Amazon S3 Glacier and S3 Compatible with data archiving object storage with immutability enabled. Amazon VPC, subnet and security group settings for an archiver appliance are configured beforehand.  |  | | --- | | {   "Version": "2012-10-17",   "Statement": [     {       "Sid": "VisualEditor0",       "Effect": "Allow",       "Action": [         "s3:DeleteObject",         "s3:PutObject",         "s3:GetObject",         "s3:RestoreObject",         "s3:ListBucket",         "s3:AbortMultipartUpload",         "s3:GetBucketVersioning",         "s3:ListAllMyBuckets",         "s3:GetBucketLocation",         "s3:GetBucketObjectLockConfiguration",         "s3:PutObjectRetention",         "s3:GetObjectVersion",         "s3:PutObjectLegalHold",         "s3:GetObjectRetention",         "s3:DeleteObjectVersion",         "s3:ListBucketVersions",         "ec2:DescribeInstances",         "ec2:CreateKeyPair",         "ec2:DescribeKeyPairs",         "ec2:RunInstances",         "ec2:DeleteKeyPair",         "ec2:DescribeVpcAttribute",         "ec2:CreateTags",         "ec2:DescribeSubnets",         "ec2:TerminateInstances",         "ec2:DescribeSecurityGroups",         "ec2:DescribeImages",         "ec2:DescribeVpcs"       ],       "Resource": "\*"     }   ]  } | |

Read-Only Permissions for Amazon S3 and S3 Compatible Object Storage

The following permissions are required to connect to Amazon S3 or S3 compatible object storage from the second backup server in case you need to perform data recovery options.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)1. Immutability Enabled

|  |  |
| --- | --- |
| These permissions apply for Amazon S3 or S3 compatible object storage with immutability enabled.  |  | | --- | | {   "Version": "2012-10-17",   "Statement": [     {       "Effect": "Allow",       "Action": [           "s3:ListBucket",           "s3:GetBucketLocation",           "s3:GetObject",           "s3:ListAllMyBuckets",           "s3:GetBucketVersioning",           "s3:GetBucketObjectLockConfiguration",           "s3:ListBucketVersions",           "s3:GetObjectVersion",           "s3:GetObjectRetention",           "s3:GetObjectLegalHold"       ],       "Resource": "\*"     }   ]  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)2. Immutability Disabled

|  |  |
| --- | --- |
| These permissions apply for Amazon S3 or S3 compatible object storage with immutability disabled.  |  | | --- | | {   "Version": "2012-10-17",   "Statement": [     {       "Effect": "Allow",       "Action": [           "s3:ListBucket",           "s3:GetBucketLocation",           "s3:GetObject",           "s3:ListAllMyBuckets",           "s3:GetBucketVersioning",           "s3:GetBucketObjectLockConfiguration",           "s3:CreateBucket",           "s3:DeleteBucket"       ],       "Resource": "\*"     }   ]  } | |

Batch Retrieval Permissions for Amazon S3 Glacier

The following permissions are required to perform standard accelerated retrieval that uses S3 Batch Operations:

|  |
| --- |
| "iam:GetRole",  "iam:CreateRole",  "iam:PutRolePolicy",  "iam:DeleteRolePolicy",  "iam:DeleteRole",  "iam:PassRole",  "s3:CreateJob",  "s3:DescribeJob” |

Permissions for Amazon EBS Encryption

If you have EBS encryption enabled in Amazon EC2, specific permissions are required for a helper appliance to perform a health check of backup files in object storage and run the [archiving job](archiving_job.md).

1. You must grant this permission to the IAM user.

|  |
| --- |
| "ec2:GetEbsEncryptionByDefault" |

1. You must grant the following permissions for the default encryption key to an IAM Role using a [Key Policy](https://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html).

|  |
| --- |
| "kms:Encrypt",  "kms:Decrypt",  "kms:ReEncrypt\*",  "kms:GenerateDataKey\*",  "kms:DescribeKey",  "kms:CreateGrant" |

Azure Archive Object Storage Permissions

The following permissions are required to use Azure Archive object storage.

|  |
| --- |
| {   "properties": {     "roleName": "CUSTOM\_ROLE\_MINIMAL\_PERMISSIONS",     "description": "CUSTOM\_ROLE\_MINIMAL\_PERMISSIONS",     "assignableScopes": [       "/subscriptions/111111-1111-1111-0000-00000000000"     ],     "permissions": [       {         "actions": [           "Microsoft.Authorization/\*/read",           "Microsoft.Compute/locations/\*",           "Microsoft.Compute/virtualMachines/\*",           "Microsoft.Compute/disks/read",           "Microsoft.Compute/disks/write",           "Microsoft.Compute/disks/delete",           "Microsoft.Network/locations/\*",           "Microsoft.Network/networkInterfaces/\*",           "Microsoft.Network/networkSecurityGroups/join/action",           "Microsoft.Network/networkSecurityGroups/read",           "Microsoft.Network/networkSecurityGroups/write",           "Microsoft.Network/networkSecurityGroups/delete",           "Microsoft.Network/publicIPAddresses/join/action",           "Microsoft.Network/publicIPAddresses/read",           "Microsoft.Network/publicIPAddresses/write",           "Microsoft.Network/publicIPAddresses/delete",           "Microsoft.Network/virtualNetworks/read",           "Microsoft.Network/virtualNetworks/write",           "Microsoft.Network/virtualNetworks/subnets/join/action",           "Microsoft.Storage/storageAccounts/listKeys/action",           "Microsoft.Storage/storageAccounts/read",           "Microsoft.Resources/deployments/\*",           "Microsoft.Resources/subscriptions/resourceGroups/read",           "Microsoft.Resources/checkResourceName/action",           "Microsoft.Resources/subscriptions/resourceGroups/write",           "Microsoft.Resources/subscriptions/locations/read"  ],         "notActions": [],         "dataActions": [],         "notDataActions": []       }     ]   }  } |

Google Cloud Object Storage Permissions

The following permissions are required to use Google Cloud Object Storage as an object storage repository.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)1. General Permissions to Add Google Cloud Object Storage

|  |  |
| --- | --- |
| The following permissions are required to use Google Cloud object storage.  |  | | --- | | {   "storage.buckets.get",   "storage.buckets.list",   "storage.objects.create",   "storage.objects.delete",   "storage.objects.get",   "storage.objects.list"  } |  Consider the following:   * The storage.buckets.list permission is not required if you specify the bucket name explicitly at the Bucket step of the [New Object Repository](adding_google_cloud_object_storage.md) wizard. * The Owner IAM role does not necessarily grant the permissions required for working with Google Cloud Storage. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)2. Permissions to Add Google Cloud Object Storage with Immutability

|  |  |
| --- | --- |
| The following permissions are required to use Google Cloud object storage if you enable [Immutability](immutability_object_storage_repositories.md) for it.  |  | | --- | | {   "storage.buckets.get",   "storage.buckets.list",   "storage.objects.create",   "storage.objects.delete",   "storage.objects.get",   "storage.objects.list"   "storage.objects.setRetention"   "storage.objects.update"  } | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)3. Read-Only Permissions for Google Cloud Object Storage

|  |  |
| --- | --- |
| The following permissions are required to connect to Google Cloud object storage from the second backup server in case you need to perform data recovery operations.  |  | | --- | | {   "storage.buckets.get",   "storage.buckets.list",   "storage.objects.get",   "storage.objects.list"  } | |

Adding Object Storage as Unstructured Data Source

The following permissions are required for the account that you use to add Amazon S3 and S3 Compatible object storage as unstructured sources.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)1. Permissions for Working with Bucket Objects

|  |  |
| --- | --- |
| To be able to work with objects in buckets, the account for Amazon S3 and S3 Compatible object storage must have the following permissions:  |  | | --- | | HeadBucket  GetBucketLocation  ListBuckets  HeadObject  GetObject  GetObjectTagging  ListObjectsV1  ListObjectsV2  ListObjectVersions | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)2. Permissions for Restoring Objects and Perform Backup Objects Calls

|  |  |
| --- | --- |
| To be able to perform restore, recovery, and backup object calls, the account for Amazon S3 and S3 Compatible object storage must have the following permissions:  |  | | --- | | PutObject  PutObjectTagging  DeleteObject  DeleteObjects  CreateMultipartUpload  CreateBucket  UploadPart  CompleteMultipartUpload  AbortMultipartUpload | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)3. Permissions for Getting Backup Bucket Properties

|  |  |
| --- | --- |
| To be able to get backup bucket properties, the account for Amazon S3 and S3 Compatible object storage must have the following permissions:  |  | | --- | | GetBucketLifecycleConfiguration  GetBucketLogging  GetBucketMetricsConfiguration  ListBucketMetricsConfigurations  GetBucketNotificationConfiguration  GetBucketOwnershipControls  GetBucketPolicy  GetPublicAccessBlock  GetBucketReplication  GetBucketRequestPayment  GetBucketTagging  GetBucketVersioning  GetBucketWebsite  GetObjectLockConfiguration | |

Storage Systems Snapshot Integration

NetApp Data ONTAP/Lenovo Thinksystem DM/DG Permissions

The account used to connect to NetApp ONTAP, Fujitsu ETERNUS HX/AX, Lenovo ThinkSystem DM/DG storage system must have permissions described in this section. The commands are provided for the console, UI names may differ.

CDOT (VMware Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
| DEFAULT | readonly |
| cluster | readonly |
| metrocluster | readonly |
| vserver fcp | readonly |
| volume file | readonly |
| lun igroup | all |
| vserver iscsi | all |
| network | readonly |
| system node | readonly |
| security | readonly |
| security login | readonly |
| set | readonly |
| snapmirror | all |
| system | readonly |
| version | readonly |
| volume qtree | readonly |
| lun | all |
| vserver nfs | all |
| volume snapshot | all |
| volume | all |
| vserver | all |

Only as SVM (VMware Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
| DEFAULT | none |
| lun | all |
| lun igroup | all |
| network | readonly |
| security | readonly |
| security login | readonly |
| snapmirror | all |
| system | readonly |
| version | readonly |
| volume | all |
| volume file | readonly |
| volume qtree | all |
| volume snapshot | all |
| vserver | all |
| vserver fcp | all |
| vserver iscsi | all |
| vserver nfs | all |

CDOT (NAS Backup Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
| DEFAULT | readonly |
| security | readonly |
| security login | readonly |
| volume snapshot | all |
| vserver | all |
| vserver nfs | all |

Only as SVM (NAS Backup Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
| DEFAULT | none |
| lun | readonly |
| network | readonly |
| security | readonly |
| security login | readonly |
| snapmirror | readonly |
| version | readonly |
| volume | readonly |
| volume snapshot | all |
| vserver | all |

CDOT (Veeam Agent Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
| cluster | readonly |
| lun | all |
| metrocluster | readonly |
| network | readonly |
| system license | readonly |
| system node | readonly |
| version | readonly |
| volume | all |
| volume snapshot | all |
| vserver | all |

Only as SVM (Veeam Agent Integration)

| Command/Directory | Access/Query Level |
| --- | --- |
| lun | all |
| network | readonly |
| version | readonly |
| volume | all |
| volume snapshot | all |
| vserver | all |

Universal Storage API Integrated Systems Permissions

The account used to connect to a Universal Storage API integrated system must be assigned a necessary role in the storage system console and have a set of necessary permissions.

* For DataCore, the account must have the following permissions:

+ General
+ Port
+ Host
+ Virtual disk
+ Snapshot
+ Physical disk

* For Dell PowerMax, the account must be assigned the Storage Administrator role.

* For Dell PowerStore, the account must be assigned one of the following roles:

+ Administrator
+ Storage Administrator
+ Storage Operator

* For Fujitsu ETERNUS AF and DX series, the account must be assigned the Software role.

* For Hitachi VSP/VSP One Block, the account must be assigned the following roles:

+ Storage Administrator (View Only)
+ Storage Administrator (Provisioning)
+ Storage Administrator (Local Copy)

* For NEC Storage M Series, the account must be assigned the Administrator role.

* For NetApp SolidFire/HCI, the account must have the following permissions:

+ Volumes
+ Cluster Admins

* For Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile), the account must be assigned the Veeam Admin Role.

For privileges required to integrate the unstructured data backup feature with Dell PowerScale (formerly Isilon), see [Integration with Dell PowerScale](nas_filer_nas_device.md#dell_emc_isilon) in the Unstructured Data Backup section.

For storage systems not mentioned above, the account must have Administrator role.

Related Topics

For permissions required for Veeam Backup Enterprise Manager, see [Permissions](https://helpcenter.veeam.com/docs/vbr/em/required_permissions.html?ver=13) in the Enterprise Manager User Guide.


