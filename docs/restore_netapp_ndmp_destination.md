---
title: "Step 3. Specify Restore Destination"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_netapp_ndmp_destination.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Restore Destination


|  |
| --- |
| Important |
| Before specifying the destination, you must create a new Data Protection (DP) volume in the target NetApp ONTAP server to be used as the destination. The DP volume must be in read-only mode. |

At the Destination step of the wizard, specify destination where the archived volumes will be restored:

1. In the This server field, select the NetApp NDMP server where the target DP volume is located. If the NetApp NDMP server is not added to the backup infrastructure yet, click Add to open the New NDMP Server wizard.
2. Click Browse next to the Type in a path to a volume field and select the target DP volume where the archived volume will be restored to.

![Step 3. Specify Restore Destination](images/netapp_ndmp_restore_destination.webp)

Page updated 2026-07-08

