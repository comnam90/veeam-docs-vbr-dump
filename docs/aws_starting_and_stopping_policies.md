---
title: "Starting and Stopping Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_starting_and_stopping_policies.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Starting and Stopping Backup Policies


You can start a backup policy manually, for example, if you want to create an additional restore point in the snapshot or backup chain and do not want to modify the configured backup policy schedule. You can also stop a backup policy if processing of an instance is about to take too long, and you do not want the policy to have an impact on the production environment during business hours.

To start or stop a backup policy, do the following:

1. In the
   Veeam Backup & Replication
    console, open the
   Home
    view.
2. Navigate to
   Jobs
   .
3. Select the necessary backup policy, and click
   Start
    or
   Stop
   on the ribbon.

Alternatively, you can right-click the selected policy, and select
Start
 or
Stop
.

[![Start and stop backup policy](images/aws_starting_policy.webp)](images/aws_starting_policy.webp "Start and stop backup policy")

Page updated 2025-07-08

