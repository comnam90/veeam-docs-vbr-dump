---
title: "Veeam VM Migrator Utility"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_migrator_utility.html"
last_updated: "10/28/2025"
product_version: "13.0.1.1071"
---

# Veeam VM Migrator Utility

In this article

Veeam Backup & Replication tracks VMs in jobs using Managed Object Reference IDs (MORef-IDs), which change after migration or recreation of vCenter, causing MORef-ID misalignment.

Veeam VM Migrator utility is integrated into Veeam Backup PowerShell module and it allows you to resolve MORef-ID misalignment. As a result, your backup incremental chains will remain intact after an inventory change in vCenter.

The utility consists of the following cmdlets:

* Set-VBRVmBiosUuid — this cmdlet updates the BIOS UUIDs of existing VM entries within the Veeam Backup & Replication configuration database based on information from the old vCenter.
* Set-VBRVCenterName — this cmdlet modifies vCenter name by adding the \_old suffix to its name.
* Generate-VBRViMigrationSpecificationFile — this cmdlet generates a migration task file which contains the list of mapping tasks.
* Start-VBRViVMMigration — this cmdlet starts MORef-IDs update.

For more information on the utility cmdlets, see [Veeam PowerShell Reference](https://helpcenter.veeam.com/docs/vbr/powershell/veeam_vm_migrator.html?ver=13) guide.

How VM Migrator Utility Works

Veeam VM Migrator utility performs migration the following way:

1. [Optional] Updates BIOS UUIDs of VMs located on the old vCenter to ensure future mapping accuracy.
2. [Optional] Renames the old vCenter name by adding the \_old suffix to its name.
3. Scans old and new vCenters for VM references, and creates mapping tasks.
4. Generates a migration task file which contains mapping tasks.
5. Uses previously generated migration task file to perform VMs MORef-IDs update.

Page updated 10/28/2025

Page content applies to build 13.0.1.1071
