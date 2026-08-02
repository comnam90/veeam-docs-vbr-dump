---
title: "Removing Worker Profiles"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_worker_profile_remove.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Worker Profiles


The backup appliance allows you to permanently remove sets of worker profiles if you no longer need them.

|  |
| --- |
| Note |
| You cannot remove a profile set if any worker instances that have been created based on this set are currently running. Wait for all the related operations to complete — and then try removing the profile set again. |

To remove a profile set from the backup appliance, do the following:

1. Switch to the Configuration page.
2. Navigate to Workers > Profile.
3. Select the profile set and click Remove.

[![Removing Worker Profiles](images/azure_removing_worker_profiles.webp)](images/azure_removing_worker_profiles.webp "Removing Worker Profiles")

Page updated 2026-07-01

