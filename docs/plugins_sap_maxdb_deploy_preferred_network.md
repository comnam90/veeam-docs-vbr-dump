---
title: "Specifying Preferred Networks for Veeam Plug-Ins"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_deploy_preferred_network.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Specifying Preferred Networks for Veeam Plug-Ins


You can specify networks over which Veeam Plug-In must transport data when you perform data protection and disaster recovery tasks on remote backup repositories. This setting applies only to Veeam Plug-In network traffic, without affecting the data traffic of other Veeam Backup & Replication components. Setting a dedicated network for Veeam Plug-In backup and replication operations can help to reduce heavy network loads.

|  |
| --- |
| Note |
| Consider the following:   * By default, if there are no specified preferred networks for Veeam Plug-In data traffic, Veeam Plug-In will connect to preferred networks specified in Veeam Backup & Replication. For details on setting preferred networks in Veeam Backup & Replication, see [Specifying Preferred Networks](select_backup_network.md). * Veeam Plug-In does not save information about failed network connections. If backup or restore operations fail, Veeam Plug-In tries to connect to the following network from the preferred networks list to finish the started operations. Regardless of the first unsuccessful connection, Veeam Plug-In will try to perform the next backup operations first on the failed network. * Veeam Plug-In network preferences take priority over Veeam Backup & Replication network preferences. Only if the preferred networks for Veeam Plug-In data traffic are not available for any reason, Veeam Plug-In will try to connect to the Veeam Backup & Replication preferred networks. |

To specify networks for data transfer, you must create a list of preferred networks. When Veeam Plug-In needs to transfer data, it uses networks from this list. If a connection over any of the preferred networks cannot be established for any reason, Veeam Plug-In will automatically fail over to the following network from the preferred networks list.

To create and manage the list of preferred networks that Veeam Plug-In will use, you can perform the following operations:

* [Adding Preferred Networks](#addntw)
* [Accessing Preferred Networks](#accessntw)
* [Removing Preferred Networks](#removentw)

Adding Preferred Networks

1. Access the Veeam Plug-In for SAP MaxDB directory /opt/veeam/VeeamPluginforSAPMaxDB on the server where Veeam Plug-In is installed.
2. Run the SapMaxDBBackintConfigTool command with the following parameter:

|  |
| --- |
| SapMaxDBBackintConfigTool --add-preferred-network <network\_IP\_address> <position\_in\_list> |

where:

* <network\_IP\_address> can be either the IP address of a single network or a network mask that contains a range of network IP addresses. Specify one of the available options to add as preferred networks for Veeam Plug-In data traffic.
* <position\_in\_list> is the position number of the network in the preferred networks list. The position in the list determines in what order Veeam Plug-In will connect to the specified network. If you do not chose a specific position in the list, newly added networks take the last place in the list automatically.

For example:

|  |
| --- |
| SapMaxDBBackintConfigTool --add-preferred-network 172.24.29.189 2 |

Accessing Preferred Networks

1. Access the Veeam Plug-In for SAP MaxDB directory /opt/veeam/VeeamPluginforSAPMaxDB on the server where Veeam Plug-In is installed.
2. Run SapMaxDBBackintConfigTool with the following parameter:

|  |
| --- |
| SapMaxDBBackintConfigTool --show-preferred-networks |

The following example shows what the output of the SapMaxDBBackintConfigTool command with the --show-preferred-networks parameter can look like:

|  |
| --- |
| SapMaxDBBackintConfigTool --show-preferred-networks  Preferred networks:  1. 172.24.29.156  2. 172.24.26.189 |

Removing Preferred Networks

1. Access the Veeam Plug-In for SAP MaxDB directory /opt/veeam/VeeamPluginforSAPMaxDB on the server where Veeam Plug-In is installed.
2. Run SapMaxDBBackintConfigTool with the following parameter:

|  |
| --- |
| SapMaxDBBackintConfigTool --remove-preferred-network <network\_IP\_address> |

where <network\_IP\_address> can be either the IP address of a single network or a network mask that contains a range of network IP addresses. Specify one of the available options to remove from the preferred networks list.

For example:

|  |
| --- |
| SapMaxDBBackintConfigTool --remove-preferred-network 172.24.29.189 |


