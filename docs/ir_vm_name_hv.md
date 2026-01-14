---
title: "Step 8. Change VM Names and UUIDs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ir_vm_name_hv.html"
last_updated: "8/13/2025"
product_version: "13.0.1.1071"
---

# Step 8. Change VM Names and UUIDs

In this article

This step is available if you recover workloads to a new location or with different settings.

At the Name step of the wizard, specify names under which VMs will be recovered and select whether you want to preserve VM UUIDs or change them. By default, Veeam Backup & Replication preserves the original names and UUIDs.

|  |
| --- |
| Note |
| We recommend that you specify a new name and generate a new UUID for a VM to prevent conflicts if the original workload still resides in the production environment. The name and UUID change is not required if the original workload no longer exists, for example, it was permanently deleted. |

Changing Names

To change a name:

1. In the Virtual machines list, select the necessary workloads and click Name.
2. In the Change Name section, enter a name explicitly or specify a change name rule by adding a prefix or suffix to the original workload name.

Alternatively, you can change a VM name directly in the Virtual machines list. To do this, click the New Name field and enter the name to be assigned to the recovered VM.

![Step 8. Change VM Names and UUIDs](images/instant_recovery_to_hv_name.webp)

Changing UUIDs

To change VM identification settings:

1. Select the necessary workloads in the list and click System UUID.
2. In the BIOS UUID Settings window, select to generate a new UUID.

![Step 8. Change VM Names and UUIDs](images/instant_recovery_to_hv_uuid.webp)

Page updated 8/13/2025

Page content applies to build 13.0.1.1071
