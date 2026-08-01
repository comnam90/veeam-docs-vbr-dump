---
title: "Adding Backup Repositories Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_repositories_add_ui.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Adding Backup Repositories Using Web UI


|  |
| --- |
| Important |
| If your backup appliance is managed by a Veeam Backup & Replication server and you add a new backup repository using the backup appliance Web UI, Veeam Plug-in for AWS will not propagate these settings to the Veeam Backup & Replication server automatically. To discover new backup repositories created on the backup appliance, follow the instructions provided in section [Connecting to Existing Repositories](aws_connecting_existing_repository.md). |

To add a backup repository, do the following:

1. [Check prerequisites and limitations](aws_repository_add_limitations.md).
2. [Launch the Add Repository wizard](aws_repository_add_launch.md).
3. [Specify a backup repository name and description](aws_repository_add_name.md).
4. [Configure backup repository settings](aws_repository_add_folder.md).
5. [Enable data encryption for the backup repository](aws_repositories_add_encryption.md).
6. [Specify an S3 interface endpoint](aws_repositories_add_s3endpoint.md).
7. [Finish working with the wizard](aws_repository_add_finish.md).

Page updated 2026-05-20

