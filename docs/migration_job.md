---
title: "Migrating VMs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/migration_job.html"
last_updated: "5/15/2024"
product_version: "13.0.1.1071"
---

# Migrating VMs


You can relocate one or more VMs with Quick Migration. Quick migration can be used to move VMs from one ESXi host to another one. You can perform "hot" Quick Migration for running VMs or "cold" Quick Migration for VMs that are powered off.

Quick Migration is not job-driven: it cannot be saved as a job or scheduled to run later. Veeam Backup & Replication will start relocating VMs immediately after you finish working with the Quick Migration wizard.

Before you start Quick Migration, [check prerequisites](quick_migration_before_you_begin.md). Then use the Quick Migration wizard to migrate VMs.

1. [Launch the Quick Migration wizard](quick_migration_launch.md).
2. [Select VMs to relocate](quick_migration_vms.md).
3. [Specify a VM destination](quick_migration_destination.md).
4. [Select infrastructure components for data transfer](quick_migration_infrastructure.md).
5. [Finish working with the wizard](quick_migration_summary.md).


