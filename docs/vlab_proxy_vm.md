---
title: "Step 5. Set Up Proxy Appliance"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vlab_proxy_vm.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Step 5. Set Up Proxy Appliance


At the Proxy step of the wizard, configure proxy appliance settings.

1. Select the Use proxy appliance in this virtual lab check box to enable automatic recovery verification of VMs. The proxy appliance acts as a gateway that provides access from the backup server to VMs in the virtual lab. If you do not select this check box, during recovery verification Veeam Backup & Replication will only start VMs in the virtual lab and perform the heartbeat test for VMs. You will have to manually test VMs or perform manual item-level restore over the VM console.
2. By default, the proxy appliance is placed on a datastore with the maximum amount of free space. The default name of the proxy appliance is the virtual lab name that you have specified at the Name step of the wizard. To change a name or a datastore for the proxy appliance, click Edit and specify a new name or choose a different datastore.
3. Click Configure and select a production network in which the proxy appliance will be created. Select IPv4 or IPv6 or use both. Specify an IP address for the proxy appliance in the production network and settings of the DNS server to be used. You can choose to automatically obtain an IP address for the backup proxy and DNS server settings or set them manually.

|  |
| --- |
| Important |
| Consider the following:   * If you assign to the proxy appliance an IP address from the same network where the backup server is located, Veeam Backup & Replication will automatically add a new route to the routing table on the backup server. If you assign to the proxy appliance an IP address from a different network, you will have to manually add a new route to the routing table on the router in the production network. If you do not add a new route, tests and application scripts will fail and you will not be able to access VMs in isolated networks. * When Veeam Backup & Replication starts a virtual lab, it verifies if the proxy appliance is available by sending a ping request to it. If the route is not added to the routing table, the SureBackup job will fail. * You cannot edit the production network after you create the virtual lab. |

1. By default, VMs in the virtual lab work in the isolated environment and do not have access to internet. If you want to let VMs in the virtual lab access the internet, select the Allow proxy appliance to act as internet proxy for virtual machines in this lab check box. In the Port field, specify a port for HTTP traffic. By default, port 8080 is used. In the Production proxy field, you can optionally specify an IP address or a fully qualified domain name of an internet-facing proxy server that VMs must use to access internet.
2. On every VM that you plan to start in the virtual lab, adjust proxy settings in the internet options. To do this, on the VM open Internet Options > Connections > LAN Settings > Proxy server and specify an IP address of the proxy appliance on the isolated network and port number.

|  |
| --- |
| Note |
| When you allow the proxy appliance to act as an internet proxy, you enable the HTTP(S) internet access for VMs in the virtual lab. The proxy appliance does not proxy other protocols (such as ICMP protocol used for ping tests) for VMs in the virtual lab. |

![Step 5. Set Up Proxy Appliance](images/vlab_proxy_appliance.webp)


