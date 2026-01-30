---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pg_csv_file_before.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before creating a protection group, consider the following prerequisites and limitations:

* When Veeam Backup & Replication performs discovery of protected computers, Veeam Backup & Replication connects to every computer added to the protection group. If you instruct Veeam Backup & Replication to perform discovery immediately after the protection group is created, make sure that all computers added to the protection group are powered on and may be accessed over the network. Otherwise, Veeam Backup & Replication will be unable to connect to a protected computer and perform the required operations on this computer.
* We recommend that you do not add a computer to a protection group by specifying a dynamic IP address assigned to this computer. If such computer receives another IP address from a DHCP server, Veeam Backup & Replication will be unable to discover the computer and perform on this computer operations defined in the protection group settings.
* We recommend that you do not add a computer to a protection group by specifying a public IP address assigned to this computer. If you add such computer to a backup policy targeted at a cloud repository, the name of the subtenant account created for the computer can contain the public IP address. This IP address will be visible to the Veeam Cloud Connect service provider who has access to subtenant account settings.
* You must not install Veeam Agent for Linux on a server that is already being used as a Veeam Backup & Replication infrastructure component.


