---
title: "Editing Profiles"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_worker_edit_profile.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Editing Profiles


For each set of worker profiles created for an AWS Region, you can modify settings specified while creating the profile set:

1. Switch to the Configuration page.
2. Navigate to Workers > Profile.
3. Select the profile set and click Edit.
4. Complete the Edit Worker Profiles wizard:

1. To change profiles that will be used to deploy workers in the selected region, follow the instructions provided in section [Adding Profiles](aws_worker_add_profile.md) (step 3.b).
2. At the Summary step of the wizard, review configuration information and click Finish to confirm the changes.

|  |
| --- |
| Note |
| If there are any worker instances that are currently involved in a backup or archive backup process in the selected region, the changes will be applied only when the process completes. |

[![Editing Worker Profiles](images/aws_worker_profile_edit.webp)](images/aws_worker_profile_edit.webp "Editing Worker Profiles")

Page updated 2026-05-20

