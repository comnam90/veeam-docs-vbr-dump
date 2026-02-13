---
title: "Step 3. Specify Active Directory Objects"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protection_group_scope_ad.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# Step 3. Specify Active Directory Objects


At this step of the wizard, select Active Directory objects that you want to add to the protection group. You can add to a protection group the following types of Active Directory objects: domain, organization unit, container, computer, cluster, or group.

To add Active Directory objects to a protection group:

1. In the Search for objects in this domain field, click Change.
2. In the Specify Domain window, specify settings of the domain whose objects you want to include in the protection group:

1. In the Domain controller or domain DNS name field, type a name of the domain controller or domain whose objects you want to include in the protection group.
2. In the Port field, specify a port number over which Veeam Backup & Replication must communicate with the domain controller. By default, Veeam Backup & Replication uses port 389.

|  |
| --- |
| Important |
| If you want to use port 636, make sure that the domain root CA certificate is properly published in the domain. Otherwise, Veeam Backup & Replication will not be able to establish a secure connection to the protection group. |

1. From the Account list, select a user account that is the member of the DOMAIN\Administrators group. If you have not set up credentials beforehand, click the Manage accounts link or click Add on the right to add credentials. For details, see [Credentials Manager](credentials_manager.md) .
2. Click OK to close the Specify Domain window.

|  |
| --- |
| NOTE |
| If you want to include a large number of computers in the protection group but do not want to use an account with domain administrator permissions in the protection group settings, consider configuring a protection group based on a list of computers imported from a CSV file. To learn more, see [Launch New Protection Group Wizard](protection_group_launch_csv.md). |

1. In the Selected objects field, click Add.
2. In the Add Objects window, select the necessary Active Directory object in the tree and click OK. You can press and hold [Ctrl] to select multiple objects at once.

To quickly find the necessary object, you can use the search field at the bottom of the Add Objects window.

1. Click the button to the left of the search field and select the necessary type of object to search for: Everything, Computer, Cluster, Organization Unit, Container or Group.
2. Enter the object name or a part of it in the search field.
3. Click the Start search button on the right or press [Enter].

![Step 3. Specify Active Directory Objects ](images/plugins_protection_group_ad_domain.webp)


