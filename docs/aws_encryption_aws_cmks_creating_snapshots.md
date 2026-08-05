---
title: "Creating Cloud-Native Snapshots"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_encryption_aws_cmks_creating_snapshots.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Creating Cloud-Native Snapshots


The process of creating cloud-native snapshots of an EC2 instance with encrypted EBS volumes and an encrypted RDS instance does not differ from the same process for an instance with unencrypted volumes. The IAM role used to create cloud-native snapshots does not require any additional permissions — the backup appliance encrypts these snapshots with the same KMS keys with which the source instance or volume is encrypted.

Page updated 2026-05-19

