---
title: "Step 7. Select Target vApp"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_cdp_failback_vapp.html"
last_updated: "11/29/2023"
product_version: "13.0.1.1071"
---

# Step 7. Select Target vApp


The Target vApp step is available if you have selected the Failback to the original VM restored in a different location option at the Destination step.

At the Target vApp step of the wizard, specify to which vApps you want to fail back from replicas. These vApps must be already restored from backups in the required location.

By default, Veeam Backup & Replication fails back the replica to the source vApps. If you want to specify the target vApp manually, perform the following steps:

1. Select a replica and click Edit.
2. In the Selects Objects window, select a vApp or vApp container to which you want to fail back.
3. Click Add.

![Step 7. Select Target vApp](images/vcd_failback_target_vapp.webp)


