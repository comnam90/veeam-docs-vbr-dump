---
title: "Protecting VM Disk Data"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_encryption_vm_backup.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Protecting VM Disk Data


The process of creating cloud-native snapshots and image-level backups of an Azure VM whose disks are encrypted with SSE or ADE does not differ from the same process for a VM with unencrypted disks. The service account used to create restore points does not require any additional permissions — Veeam Backup for Microsoft Azure saves these restore points to backup repositories as is, without applying any additional encryption mechanisms. However, you can enable encryption at the repository level; for more information, see [Backup Repository Encryption](azure_repo_encryption.md).

Page updated 2025-08-19

