---
title: "Creating Object Storage Backup Jobs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_backup_job.html"
last_updated: "6/28/2024"
product_version: "13.0.1.1071"
---

# Creating Object Storage Backup Jobs


To protect an object storage repository, configure an object storage backup job. The backup job defines how, where and when to back up data from the object storage. One job can be used to protect one or more object storage repositories. Jobs can be started manually or scheduled to run automatically at a specific time.

Object storage backup jobs are used to protect the following sources of unstructured data:

* [S3 compatible object storage](os_s3_compatible_add.md)
* [Amazon S3 object storage](os_aws_add.md)
* [Microsoft Azure Blob storage including Azure Data Lake storage Gen2](os_azure_add.md)

Before you create an object storage backup job, check [prerequisites](os_before_you_begin.md).

To create an object storage backup job, use the New Object Storage Backup Job wizard:

1. [Launch the New Object Storage Backup Job wizard](os_backup_job_launch.md).
2. [Specify the job name and description](os_backup_job_name.md).
3. [Select objects to back up](os_backup_job_objects.md).
4. [Specify backup repository settings](os_backup_job_target_repository.md).
5. [Specify advanced backup settings](os_backup_job_advanced_settings.md).
6. [Specify archive repository settings](os_backup_job_archive_repository.md).
7. [Specify secondary repository settings](os_backup_job_secondary_repository.md).
8. [Define the job schedule](os_backup_job_schedule.md).
9. [Finish working with the wizard](os_backup_job_finish.md).


