---
title: "Veeam Backup Validator"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_validator.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Veeam Backup Validator

In this article

Veeam Backup Validator is an utility that verifies the integrity of a backup file without extracting VM data. Veeam Backup Validator is a command-prompt CRC check utility that tests a backup at the file level. You may need this utility to check whether backup files were damaged: for example, after hardware failures occurred in a backup storage side or if backup files were transferred over network.

For integrity validation, Veeam Backup Validator uses the checksum algorithm. When Veeam Backup & Replication creates a backup of a VM, it calculates a checksum for every data block in the backup file and attaches these checksums to data blocks. Veeam Backup Validator recalculates checksums for data blocks and compares them against the initial checksum values. If the results match, the backup file is viable.

Related Topics

[Using Veeam Backup Validator](backup_validator_validate.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
