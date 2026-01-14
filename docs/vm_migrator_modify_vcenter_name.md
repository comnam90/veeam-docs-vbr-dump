---
title: "Step 3. Modify Old VMware vCenter Name"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_migrator_modify_vcenter_name.html"
last_updated: "2/11/2025"
product_version: "13.0.1.1071"
---

# Step 3. Modify Old VMware vCenter Name

In this article

This is an optional step that modifies the old vCenter name by adding the \_old suffix to its name. Perform this step if the new vCenter has not been added yet, and it will have the same name as the old vCenter.

To rename the old vCenter, run the Set-VBRVCenterName cmdlet and specify the OldVCenterName parameter value.

This example shows how to rename the vCenter named vcenter70.

|  |
| --- |
| Set-VBRVCenterName -OldVCenterName "vcenter70" |

Page updated 2/11/2025

Page content applies to build 13.0.1.1071
