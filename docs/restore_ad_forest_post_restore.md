---
title: "Post-Restore Actions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_ad_forest_post_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Post-Restore Actions


After recovery completes, depending on your environment, you may need to perform the following actions manually:

* Redeploy additional domain controllers in each domain. Veeam Backup & Replication restores one domain controller per domain, so you must rebuild any additional domain controllers that the domain originally had.
* Redistribute the FSMO roles across domain controllers. The restored domain controller holds all FSMO roles, so move the roles to other domain controllers to match your intended role placement.
* Add additional global catalogs as configured in the original backup. Veeam Backup & Replication enables the global catalog only on the restored domain controllers, so you must add it to any additional domain controllers that originally hosted a global catalog.

Page updated 2026-07-31

