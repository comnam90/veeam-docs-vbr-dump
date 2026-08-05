---
title: "Step 5. Configure Restore Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/add_new_role_restore_permissions_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Configure Restore Permissions


At the Restore Permissions step of the wizard, define which backups and restore operations are available:

* Backup scope:

* All backups — allows restores from all available backups regardless of their ownership.
* Own backups only — restricts restores to backups created by users assigned to this role. You can additionally allow restoring backups from specific repositories. Click Add to select specific repositories.

* Restore options:

* All available restore options — grants access to all restore types.
* Only the following restore options — restricts access to selected restore operations (for example, Instant Recovery to VMware vSphere or Microsoft Hyper-V). Use check boxes in the list of restore options to specify the allowed restore types.

![Step 5. Configure Restore Permissions](images/add_new_role_restore_permissions_web.webp)

Page updated 2026-06-25

