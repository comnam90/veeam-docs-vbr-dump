---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_protection_group_before.html"
last_updated: "8/13/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before creating a protection group, consider the following prerequisites and limitations:

1. The protection group for MongoDB is designed to back up MongoDB replica sets. Other protection groups cannot create a volume-level backup of MongoDB data.
2. You must add nodes of a MongoDB replica set to the same protection group. Otherwise, Veeam Backup & Replication will not have complete information about the MongoDB replica set.
3. After a node of a MongoDB replica set is added to the backup scope of the protection group, Veeam Backup & Replication automatically deploys Veeam Agent and other Veeam components on this node. If you do not want to install Veeam components on a particular node, do not include it in the backup scope. For details, see [Specify Computers](mongo_protection_group_scope_computers.md).
4. When Veeam Backup & Replication performs discovery of protected computers, Veeam Backup & Replication connects to every computer added to the protection group. If you instruct Veeam Backup & Replication to perform discovery immediately after the protection group is created, make sure that all computers added to the protection group are powered on and may be accessed over the network. Otherwise, Veeam Backup & Replication will be unable to connect to a protected computer and perform the required operations on this computer.
5. Do not add a computer to a protection group by specifying a dynamic IP address assigned to this computer. If such computer receives another IP address from a DHCP server, Veeam Backup & Replication will be unable to discover the computer and perform on this computer operations defined in the protection group settings.
6. We recommend that you include each object you want to protect in one protection group only. For example, if you have added a MongoDB replica set to a protection group, it is not recommended to add a computer that is included in this replica set to another protection group. Adding computers to multiple protection groups with different computer discovery and deployment settings will result in additional load on the backup server.
7. You cannot back up the same computer with an application backup policy for MongoDB and a Veeam Agent backup policy. If you plan to create an application-level backup of MongoDB data on the computer and this computer is already protected with a Veeam Agent backup policy, delete this computer from the backup scope of the Veeam Agent backup policy. For details, see [Editing Veeam Agent Backup Policy Settings](agent_policy_edit.md).

Alternatively, if you need to create an image-level backup of a node in a MongoDB replica set, you can exclude this node from the backup scope of the protection group for MongoDB. In this case it can be backed-up with Veeam Agent backup policy. For details on how to exclude the node from the backup scope, see [Specify Computers](mongo_protection_group_scope_computers.md).

1. Veeam Backup & Replication does not support usage of a Linux account for which system settings modify shell output results to connect to a computer included in the protection group. For example, this includes Linux accounts with the modified PS1 shell variable.


