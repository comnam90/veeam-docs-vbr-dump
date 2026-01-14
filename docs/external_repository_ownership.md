---
title: "Ownership"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/external_repository_ownership.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Ownership

In this article

Ownership defines what entity can own an Amazon S3, Google Cloud\* or Azure Blob storage repository at a time.

How Does Taking Ownership Occur

After [Veeam Backup for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/overview.html?ver=10), [Veeam Backup for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/welcome.html?ver=7)\* or [Veeam Backup for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/overview.html?ver=8.1) has finished its initial backup job session, it becomes the rightful owner of both a storage repository and backup files in that repository.

Taking ownership of such a repository along with its backup files by the Veeam Backup & Replication client consists of the following consecutive steps:

* Step 1. Taking ownership of a repository.

Reclaiming ownership of a repository occurs every time a client adds object storage as an external repository to the Veeam Backup & Replication console.

* Step 2. Taking ownership of backup files in the repository.

Becoming an owner of backup files in object storage is only possible after Veeam Backup for AWS, Veeam Backup for Google Cloud\* or Veeam Backup for Microsoft Azure launches the backup job session which is referring to backups you are trying to take ownership of (for example, backup files that are located in the repository you have added at the step one).

During its session, Veeam Backup for AWS, Veeam Backup for Google Cloud\* or Veeam Backup for Microsoft Azure verifies the owner of a repository and if it finds out that the owner has been changed, it changes the owner of each backup file in that repository by creating a new checkpoint that refers to a new rightful owner. Such a checkpoint will be used during subsequent sessions of a backup job to repeat owner verification.

It is possible, however, that after you add an external repository, you never launch the associated backup job again. In such a scenario, Veeam Backup & Replication will not be able to manage retention policies, but you will still be able to restore external repository data, remove backups from external repositories and perform backup copy.

Taking Ownership by Another Veeam Backup & Replication Client

Ownership of a repository along with its backup files can only be granted to one Veeam Backup & Replication client at a time.

Therefore, if a client A adds an external repository that has previously been added by the client B, the client B completely loses its ownership privileges.

Losing privileges means that the client B will no longer be able to manage retention policies. All the previously created backup copy jobs and restore sessions will be failing.

Ownership, however, can easily be reclaimed by re-adding the same object storage anew.

\*This feature is available for Microsoft Windows-based backup servers.

Related Topics

* [Managing Retention Policy](external_repository_retention.md)
* [Adding External Repositories](external_repositories_add.md)

Page updated 10/20/2025

Page content applies to build 13.0.1.1071
