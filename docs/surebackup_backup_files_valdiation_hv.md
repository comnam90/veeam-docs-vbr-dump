---
title: "Backup File Validation"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_backup_files_valdiation_hv.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Backup File Validation

In this article

In addition to predefined tests, Veeam Backup & Replication allows you to perform backup file validation. For backup file validation, Veeam Backup & Replication performs a CRC check for backup files of machines verified by the SureBackup job. You can also validate backup files for machines from the application group with this test.

To validate the backup file, Veeam Backup & Replication uses the checksum algorithm. When Veeam Backup & Replication creates a backup file for a machine, it calculates a checksum for every data block in the backup file and stores this data in the backup file, together with machine data. During the backup file validation test, Veeam Backup & Replication decompresses the backup file, recalculates checksums for data blocks in the decompressed backup file and compares them with initial checksum values. If the results match, the test is passed.

The backup file validation test is started after recovery verification tests. As soon as Veeam Backup & Replication completes all "live" verification for all machines in the SureBackup job, it unpublishes machines and starts the backup file validation test.

The result of the backup file validation test impacts the state of the SureBackup job session. If the verification tests are completed successfully but the backup validation is not passed, Veeam Backup & Replication marks the SureBackup job session with the Failed status.

Page updated 9/3/2025

Page content applies to build 13.0.1.1071
