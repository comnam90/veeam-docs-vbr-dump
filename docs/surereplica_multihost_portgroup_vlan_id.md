---
title: "Port Groups and VLAN IDs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surereplica_multihost_portgroup_vlan_id.html"
last_updated: "1/26/2024"
product_version: "13.0.1.1071"
---

# Port Groups and VLAN IDs


You need to be extremely careful when specifying port group and VLAN ID settings for the advanced multi-host virtual lab.

Port Groups in Advanced Multi-Host Virtual Labs

For the advanced multi-host virtual lab, Veeam Backup & Replication uses an existing DVS that was configured by the backup administrator beforehand. Veeam Backup & Replication creates a number of new port groups on the DVS, one per isolated network in the virtual lab.

When Veeam Backup & Replication creates a new port group, it performs a check for the DVS selected for the virtual lab:

* If a port group with the specified name already exists, Veeam Backup & Replication starts using it for the virtual lab. However, in this case, Veeam Backup & Replication will not be the owner of this port group.
* If a port group with the specified name does not exist, Veeam Backup & Replication creates it and becomes the owner of the created port group.

When a virtual lab is removed, Veeam Backup & Replication checks the ownership of the port group:

* If Veeam Backup & Replication is not the owner of the port group, the port group remains on the DVS. Veeam Backup & Replication stops using it.

* If Veeam Backup & Replication is the owner of the port group, Veeam Backup & Replication removes this port group from the DVS.

Several virtual labs can use the same port group. For this reason, you should be extremely careful when removing virtual labs. If Veeam Backup & Replication is the owner of the virtual lab and the port group is removed, other virtual labs using this port group may fail to start.

VLAN IDs in Advanced Multi-Host Virtual Labs

A DVS port group has VLAN ID settings. If you select an existing port group for the virtual lab, you must specify its VLAN ID in the virtual lab settings.

* If VLAN ID settings are specified correctly, Veeam Backup & Replication will be able to configure the virtual lab and verify VM replicas in it.

* If VLAN ID settings are specified incorrectly, Veeam Backup & Replication will report an error informing that the selected port group exists but cannot be used due to incorrect VLAN ID settings.


