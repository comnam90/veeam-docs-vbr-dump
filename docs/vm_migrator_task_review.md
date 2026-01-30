---
title: "Step 6. Review Migration Task File"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_migrator_task_review.html"
last_updated: "2/11/2025"
product_version: "13.0.1.1071"
---

# Step 6. Review Migration Task File


After you generate the migration task file, you must carefully review and edit it. The file contains several sections with mapping tasks. Each line contains source VM MORef-ID, source VM name and BIOS UUID field values. These field values are followed by target VM MORef-ID and target VM name.

Migration Task File Sections

| Section | Description |
| --- | --- |
| hosts names | This section lists vCenter server names (old and new). |
| solid | This section lists VMs which exist in the old vCenter and in the new vCenter with the same names and BIOS UUIDs. |
| probable | This section lists the following:   * VMs with the same BIOS UUID but with different names. * VMs with the same name but different BIOS UUIDs. * VMs which have more than one instance of the same VM name and BIOS UUID present in the database. |
| old duplicates | For entries having several database records with the same name and BIOS UUID, mapping is defined only for the VMs which last restore point is the newest restore point. The rest of such objects fall into the old duplicates section. Mapping for these objects is not defined. |
| already migrated | This section lists VMs which are already linked to the new vCenter, with the names and BIOS UUIDs matching the current values on the new vCenter. Mapping for these objects is not defined. |
| not found | This section lists all VMs that did not fall into other sections but previously existed in the old vCenter. Mapping for these objects is not defined. |

When editing migration task file, consider the following:

* In the migration task file field values must be separated by a tab.
* If you need to comment out a line, use a tab followed by double slash character “//”.
* If task file contains multiple mappings for the same VM, they will be commented out. Uncomment one of them if you want to apply it.


