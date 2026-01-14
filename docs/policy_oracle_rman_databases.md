---
title: "Step 3. Specify Databases"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/policy_oracle_rman_databases.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Step 3. Specify Databases

In this article

At the Databases step of the wizard, select protection groups, computers, database systems or individual databases whose data you want to back up.

You can add to the backup scope one or more objects added to inventory in the Veeam Backup & Replication console.

Application policies with protection groups are dynamic in their nature. If Veeam Backup & Replication discovers a new computer in a protection group after the policy is created, Veeam Backup & Replication will automatically update the policy settings to include the added computer.

Adding Objects from Inventory

To add objects to the application backup policy:

1. Click Add.
2. In the Select Objects window, select one or more objects in the list and click OK. You can select any of the following objects:

* Protection group
* Computer
* Oracle home
* Oracle database

You can press and hold [Ctrl] to select multiple objects at once.

|  |
| --- |
| Note |
| In the Select Objects window, Veeam Backup & Replication shows only those computers on which Veeam Backup & Replication have detected Oracle database systems during the rescan job. To learn more, see [Rescan Job](rescan_job.md). |

To quickly find the necessary object, use the search field at the bottom of the Select Objects window.

1. Enter the object name or a part of it in the search field.
2. Click the Start search button on the right or press [Enter].

![Step 3. Specify Databases](images/policy_rman_databases_add.webp)

Excluding Objects

You can exclude protection groups, individual computers or databases from the backup scope of the application backup policy. This may be useful if you want to back up a certain database with another application backup policy.

To exclude protection groups, individual computers or databases from the backup scope:

1. Click Exclusions.
2. In the Exclusions window, select one or more objects in the list and click OK. You can select any of the following objects:

* Computer
* Oracle home
* Oracle database

You can press and hold [Ctrl] to select multiple objects at once.

|  |
| --- |
| Note |
| In the Exclusions window, Veeam Backup & Replication shows only those objects which were already added to the backup scope. To learn more, see [Adding Objects from Inventory](#add). |

![Step 3. Specify Databases](images/policy_rman_databases_exclude.webp)

Page updated 9/3/2025

Page content applies to build 13.0.1.1071
