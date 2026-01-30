---
title: "Step 4. Select Mount Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/instant_disk_recovery_mount_mode.html"
last_updated: "3/24/2025"
product_version: "13.0.1.1071"
---

# Step 4. Select Mount Mode


This step is not available if you restore VMware vSphere VM disks from a storage snapshot.

At the Mount Mode step of the wizard, select the VM disk option to register virtual disks on a VM added to an ESXi host.

If you want to register virtual disks on a cluster as FCDs, select the First class disk (FCD) option. In this case, steps of the wizard differ and Veeam Backup & Replication performs Instant FCD Recovery as described in section [Performing Instant First Class Disk (FCD) Recovery](performing_instant_fcd_recovery.md).

![Step 4. Select Mount Mode](images/instant_disk_recovery_mount_mode.webp)


