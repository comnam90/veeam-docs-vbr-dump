---
title: "Step 3. Specify Active Directory Objects"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protection_group_ad_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Specify Active Directory Objects


At the Active Directory step of the wizard, select Active Directory objects that you want to add to the protection group. You can add to a protection group the following types of Active Directory objects: domain, organizational unit, container, computer, failover cluster, or group.

To add Active Directory objects to a protection group:

1. In the Domain field, click Change.
2. In the Specify Domain window, specify settings of the domain whose objects you want to include in the protection group:

1. In the Domain controller or domain DNS name field, type a name of the domain controller or domain whose objects you want to include in the protection group.
2. In the Port field, specify a port number over which Veeam Backup & Replication must communicate with the domain controller. By default, Veeam Backup & Replication uses port 389.

If you want to use port 636, make sure that the domain Root CA certificate is properly published in the domain. Otherwise, Veeam Backup & Replication will not be able to establish a secure connection to the protection group.

1. From the Account list, select a user account that has read access permissions to all hosts with the required AD objects. If you have not set up credentials beforehand, click the Manage Accounts link or click Add on the right to add credentials.
2. Click OK to close the Specify Domain window.

1. Under Selected objects, click Add.
2. In the Active Directory Objects window, select the necessary Active Directory object in the tree, or press and hold [Ctrl] to select multiple objects at once, and click OK.

To quickly find the necessary object, you can use the search field at the top of the Active Directory Objects window.

1. Click the drop-down list to the left of the search field and select the necessary type of object to search for: Everything, Computer, Cluster, Organization unit, Container, or Group.
2. Enter the object name or a part of it in the search field and press [Enter].

You can also modify the list of selected objects in the following way:

* To remove an object from the list, select the object and click Remove.

[![Specify Active Directory Objects](images/protection_group_ad_domain_web.webp)](images/protection_group_ad_domain_web.webp "Specify Active Directory Objects")

Page updated 2026-07-01

