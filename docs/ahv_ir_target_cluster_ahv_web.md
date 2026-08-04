---
title: "Step 4. Specify Target Cluster"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_ir_target_cluster_ahv_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Specify Target Cluster


At the Cluster step of the wizard, choose the cluster to which the recovered VM will belong. In the Prism Central deployment, you can also choose whether you want the recovered VM to be assigned the same categories as the original VM.

For a cluster to be displayed in the list of the available clusters, it must be added to the backup infrastructure as described in section [Adding Nutanix AHV Server to Backup Infrastructure](ahv_add_ahv_cluster.md).

|  |
| --- |
| Important |
| If a selected VM has an attached volume group, the disks of the volume group will not be restored. |

[![Step 4. Specify Target Cluster](images/ahv_ir_target%20cluster_web.webp)](images/ahv_ir_target%20cluster_web.webp)

Page updated 2026-07-13

