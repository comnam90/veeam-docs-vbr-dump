---
title: "Backup Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_backup_chain_vpc.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup Chain


During every backup session, the backup appliance creates a restore point with backed-up VPC configuration data for each AWS Region protected by the VPC Configuration Backup policy. The restore point contains encrypted metadata that includes information on the date and time when the policy ran, AWS Regions whose VPC configuration settings were backed up by the policy, and AWS accounts whose IAM roles were used to collect VPC configuration settings for each AWS Region.

A sequence of restore points created during a set of backup sessions makes up a VPC configuration backup chain for each configuration record.

[![VPC Backup Chain](images/aws_vpc_backups_chain.webp)](images/aws_vpc_backups_chain.webp "VPC Backup Chain")

You cannot delete specific restore points created for a configuration record — these points are removed automatically according to the specified [retention policy settings](aws_vpc_policy_retention.md). However, you can manually remove a configuration record with all restore points created for it, as described in section [Removing VPC Configuration Backups](aws_backups_remove_vpc.md).

Related Topics

[VPC Configuration Backup Retention](aws_retention_backup_vpc.md)

Page updated 2026-05-19

