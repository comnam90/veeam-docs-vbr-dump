---
title: "Step 3. Select Restore Points"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uni_cdp_failover_point.html"
last_updated: "10/28/2025"
product_version: "13.0.1.1071"
---

# Step 3. Select Restore Points


At the Virtual Machines step of the wizard select to which state of replicas you want to fail over:

1. In the Machines to failover list, select the necessary workload and click Point.
2. In the Restore Points window, select whether you want to fail over to the latest available crash-consistent restore point, to the latest long-term application-consistent restore point or to a specific point in time.

To restore to a short-term restore point, select a point in the green area. The darker the green, the more I/O load was produced on the source workload. To restore to a crash-consistent, select a violet vertical bar with a circle at the top.

If you fail over to a specific point in time, use the right and left arrows on the keyboard to select the required restore point. To quickly find a long-term restore point, click a link that shows a date. In the opened window, you will see a calendar where you can select the necessary day. In the Timestamp section, you will see long-term restore points created during the selected day.

![Step 3. Select Restore Points](images/uni_cdp_failover_point.webp "Select restore point")


