---
title: "Step 9. Configure Helper Appliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ir_appliance_hv.html"
last_updated: "3/11/2025"
product_version: "13.0.1.1071"
---

# Step 9. Configure Helper Appliance

In this article

This step is available if you recover workloads with Linux OS and recover them to a new location or with different settings.

Veeam Backup & Replication recovers Linux machines using a helper appliance. The helper appliance is an auxiliary Linux-based VM registered by Veeam Backup & Replication. The appliance is quite small — around 100 MB. It requires 1024 MB RAM and takes around 10 seconds to boot.

At the Helper Appliance step of the wizard, configure the helper appliance network settings:

1. [For multiple machines] In the Network list, expand a host and select one machine for which you want to configure the helper appliance.
2. Click the Configure button.
3. In the Network Settings window, select a network for the helper appliance.

1. Click the Browse button to the right of the Production network field.
2. In the Select Network window, Veeam Backup & Replication shows a list of networks to which the target host is connected. In this list, select a network to which the helper appliance must be connected. Click OK.

Consider that the backup server and the mount server must have access to the helper appliance over the network.

1. In the VLAN ID field, specify an ID of a VLAN where the helper appliance will reside.

The 0 value means that the VLAN is not set.

1. Specify IP addressing settings for the helper appliance and DNS server:

1. Click Configure.
2. Switch to the IPv4 or IPv6 tab depending on which addresses you want to configure. Note that you can use IPv6 addresses only if IPv6 communication is enabled as described in section [IPv6 Support](ipv6.md).
3. Select the Enable IPv4/IPv6 interface check box.
4. Configure IP settings for the helper appliance:

* If you use a DHCP server in the network and want to obtain the IP address automatically, leave the Obtain an IP address automatically option selected.

* To manually assign a specific IP address to the helper appliance, click Use the following IP address and specify the IP address settings.

1. Configure IP settings for the DNS server:

* If you use a DHCP server in the network and want to obtain the IP address automatically, leave the Obtain DNS server address automatically option selected.

* To manually assign a specific IP address to the DNS server, click Use the following DNS server address and specify preferred and alternate addresses.

1. Click OK.

![Step 9. Configure Helper Appliance](images/instant_recovery_to_hv_helper.webp)

Page updated 3/11/2025

Page content applies to build 13.0.1.1071
