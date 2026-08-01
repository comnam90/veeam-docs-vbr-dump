---
title: "Deploying Backup Appliance"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_deploying_appliances.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Deploying Backup Appliance


|  |
| --- |
| Notes |
| * This section is intended for IT managers, virtual infrastructure administrators, backup administrators and other IT professionals who plan to deploy and use Veeam Plug-in for AWS. * This section assumes that users have basic knowledge of AWS EC2, Managing VPCs and understanding AWS IAM. |

To deploy a new backup appliance from the Veeam Backup & Replication console, do the following:

1. [Launch the New Veeam Backup for AWS Appliance wizard](aws_deploy_appliance_launch.md).
2. [Choose a deployment mode](aws_deploy_appliance_mode.md).
3. [Specify an AWS account in which the appliance will be deployed](aws_deploy_appliance_account.md).
4. [Specify a name and description for the appliance](aws_deploy_appliance_instance.md).
5. [Specify the connection type](aws_deploy_ip_settings.md).
6. [Specify network settings for the appliance](aws_deploy_network_resources.md).
7. [Specify credentials for the default user account](aws_deploy_guest_os_credentials.md).
8. [Wait for the appliance to be added to the backup infrastructure](aws_deploy_appliance_apply.md).
9. [Finish working with the wizard](aws_deploy_appliance_finish.md).

How Deployment Works

When deploying a backup appliance, Veeam Backup & Replication performs the following steps:

1. Deploys an EC2 instance from the Ubuntu 22.04 LTS image.
2. Creates a temporary Amazon S3 bucket in AWS and uploads backup appliance installation packages and their dependencies to the bucket.
3. Installs the [required software components](aws_backup_appliances.md) on the EC2 instance.
4. Creates the following IAM roles in AWS and adds them to the EC2 instance:

* Impersonation IAM role — will be attached to the backup appliance and then used to assume other IAM roles added to the appliance.
* Default Backup Restore IAM role — will be used to perform data protection and recovery operations within the AWS account to which the backup appliance belongs. Out of the box, the role is already assigned all the required permissions listed in section [Full List of IAM Permissions](aws_full_list_permissions.md).

You will be able to add other IAM roles later, after the backup appliance installation. For more information, see [Managing IAM Roles](aws_accounts_iam_roles.md).

1. Removes the temporary Amazon S3 bucket from AWS.

Related Topics

[Connecting to Existing Appliances](aws_connect_appliance.md)

Page updated 2026-06-30

