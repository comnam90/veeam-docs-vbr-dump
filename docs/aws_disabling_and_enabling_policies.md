---
title: "Enabling and Disabling Backup Policies"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_disabling_and_enabling_policies.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Enabling and Disabling Backup Policies


By default, Veeam Backup & Replication runs all created backup policies according to the specified schedules. However, you can temporarily disable a backup policy so that Veeam Backup & Replication does not run the backup policy automatically. You will still be able to [manually start](aws_starting_and_stopping_policies.md) or enable the disabled backup policy at any time you need.

To disable an enabled backup policy or to enable a disabled backup policy, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. Navigate to Jobs.
3. Select the necessary backup policy and click Disable on the ribbon.

Alternatively, you can right-click the necessary backup policy and select Disable.

[![Enable and disable backup policy](images/aws_disable_policy.webp)](images/aws_disable_policy.webp "Enable and disable backup policy")

Page updated 2026-05-21

