---
title: "Step 5. Generate Migration Task File"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_migrator_task_generate.html"
last_updated: "2/11/2025"
product_version: "13.0.1.1071"
---

# Step 5. Generate Migration Task File

In this article

To generate the migration task file, run the Generate-VBRViMigrationSpecificationFile cmdlet and specify the ExportPath, NewVCenterName,and OldVCenterName parameter values.

This example shows how to generate the migration task file for the old vCenter named vcenter70\_old and the new vCenter named vcenter70. The migration task file will be generated at the following path: C:\Folder.

|  |
| --- |
| Generate-VBRViMigrationSpecificationFile -ExportPath C:\Folder -NewVCenterName vcenter70 -OldVCenterName vcenter70\_old |

Page updated 2/11/2025

Page content applies to build 13.0.1.1071
