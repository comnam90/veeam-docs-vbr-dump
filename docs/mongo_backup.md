---
title: "MongoDB Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_backup.html"
last_updated: "12/10/2025"
product_version: "13.0.1.1071"
---

# MongoDB Backup


MongoDB Backup is a backup solution integrated in Veeam Backup & Replication that allows you to back up MongoDB replica sets. With this solution, Veeam Backup & Replication installs Veeam components on MongoDB nodes, backs up volumes with MongoDB data and transfers backups to backup repositories configured in Veeam Backup & Replication.

Database administrators can use Veeam Backup & Replication to create volume-level backups of MongoDB data. Compared to image-level backups, MongoDB Backup offers more flexible scenarios for database backup. In particular, MongoDB Backup users can back up MongoDB data and operations log (oplog), configure independent backup schedules for full and incremental backups, restore and publish MongoDB instances and restore MongoDB collections.

In This Section

* [Overview](mongo_about.md)
* [Planning and Preparation](mongo_planning_and_preparation.md)
* [Getting Started](mongo_getting_started.md)
* [Configuring Security Settings for MongoDB Backup](mongo_security_settings.md)
* [Working with Protection Group](mongo_protection_group.md)
* [Working with Application Backup Policy](mongo_policy.md)
* [Managing Protected Replica Sets](mongo_protected_replica_sets.md)
* [Managing Protected Computers](mongo_protected_computers.md)
* [Managing Application Backups](mongo_application_backups.md)
* [Reporting](mongo_report.md)
* [Restoring with Veeam Explorer for MongoDB](mongo_restore.md)
* [Publishing with Veeam Explorer for MongoDB](mongo_publish.md)
* [Retention of MongoDB Backups](mongo_retention.md)
* [Logs and Support](mongo_veeam_logs.md)


