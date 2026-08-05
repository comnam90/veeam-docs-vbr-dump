---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_repository_add_limitations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


When adding a backup repository to the backup appliance, keep in mind the following limitations and considerations.

Amazon S3 Bucket

Before you add a backup repository, check the following prerequisites:

* An Amazon S3 bucket must be created in AWS beforehand as described in [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/creating-bucket.html).
* If you have any S3 Lifecycle configuration associated with the selected Amazon S3 bucket, it is recommended that you limit the scope of lifecycle rules applied to Amazon S3 objects in the bucket so that no rules are applied to backup files created by the backup appliance. Otherwise, the files may be unexpectedly deleted or transitioned to another storage class, and the appliance may not be able to access the files. For more information on managing S3 Lifecycle configurations, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/how-to-set-lifecycle-configuration-intro.html).

|  |
| --- |
| Important |
| To maintain the security of your data, you should never use a public S3 bucket as a repository for Veeam Plug-in for AWS. For more information on creating buckets, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/creating-bucket.html). |

Repository Folder

If you plan to select an existing folder for storing backup files, consider the following:

* The folder must not be specified as a backup repository on multiple backup appliances simultaneously. Retention sessions running on different backup appliances may corrupt backup files stored in the folder, which may result in unpredictable data loss.
* The created backup repository will have the storage class that has been specified when creating the folder. You cannot change the storage class for the repository.
* If encryption at the repository level is enabled for the selected folder, it will be required to provide a password or an encryption key for this folder at [step 4](aws_repositories_add_encryption.md) of the wizard.
* If the selected folder already contains image-level backups created by the Veeam backup service, the backup appliance will import the backed-up data to the appliance configuration database. You can then use this data to perform all disaster recovery operations described in section [Performing Restore](aws_recovery.md).

By default, the backup appliance applies retention settings saved in the backup metadata to the imported image-level backups. However, if the selected folder contains backups of resources that you plan to protect by a backup policy with the created repository specified as a backup target, the backup appliance will rewrite the saved retention settings and will apply to the imported backups new retention settings configured for that backup policy.

Immutability

If you plan to add a repository with immutability enabled, keep in mind the following limitations:

* S3 Object Lock and S3 Versioning must be enabled for an Amazon S3 bucket in which the repository will be located. The default retention period must not be configured in the Object Lock settings. For more information on the S3 Versioning and S3 Object Lock features, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/managing-storage.html).

* Veeam Plug-in for AWS does not support changes made to immutability settings in the AWS Management Console for buckets that are already used as target locations for image-level backups.

* An IAM role that you plan to specify to create the repository and further to access the repository when performing data protection and recovery tasks must be assigned permissions to collect immutability settings of Amazon S3 buckets and to create immutable backups. For more information on the required permissions, see [Repository IAM Role Permissions](aws_role_permissions_repo.md).

* You cannot store indexes of EFS file systems and backups of the appliance configuration database in the repository with immutability enabled.
* You cannot remove immutable data manually using the backup appliance Web UI, as described in sections [Removing EC2 Backups and Snapshots](aws_backups_remove.md), [Removing RDS Backups and Snapshots](aws_snapshots_remove_rds.md) and [Removing VPC Configuration Backups](aws_backups_remove_vpc.md).
* You can neither remove immutable data from AWS using any cloud service provider tools nor request the technical support department to do it for you. Since Veeam Plug-in for AWS uses S3 Object Lock in the compliance mode, none of the protected objects can be overwritten or deleted by any user, including the root user in your AWS account. For more information on S3 Object Lock retention modes, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html#object-lock-retention-modes).

Encryption

If you plan to enable encryption for a backup repository, consider the following:

* After you create a repository with encryption enabled, you will not be able to disable encryption for this repository. However, you will still be able to change the encryption settings as described in section [Editing Backup Repository Settings](aws_repositories_edit.md).
* If you enable encryption for a repository where EC2 image-level backups are stored when editing the repository, this will affect the creation of an existing backup chain — the next sequence of backups will be a full backup instead of an incremental backup. After creating the full backup, the backup appliance will continue to copy only those data blocks that have changed since the previous backup session.
* If you choose to encrypt data using an AWS KMS key, keep in mind that:

* AWS managed keys cannot be used to encrypt data stored in repositories due to [AWS limitations](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#aws-managed-cmk).
* Only symmetric KMS keys are supported.
* Do not disable KMS keys specified in the repository settings. Otherwise, the backup appliance will not be able to encrypt data, and backup policies that store backups in these repositories will fail to complete successfully.
* Do not delete KMS keys specified in the repository settings. Otherwise, the backup appliance will not be able to decrypt data stored in these repositories.

If a KMS key is scheduled for deletion, it will acquire the Pending deletion state. In this case, the backup appliance will raise the warning notifying that you must either change the encryption settings for the backup repository in the backup appliance or cancel the key deletion during the following 7 days.

For more information on managing AWS KMS keys, see [AWS Documentation](https://docs.aws.amazon.com/kms/latest/developerguide/enabling-keys.html).

Page updated 2026-06-22

