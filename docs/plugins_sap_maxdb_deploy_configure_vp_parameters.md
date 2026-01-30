---
title: "Configuration Tool Parameters"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_deploy_configure_vp_parameters.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Configuration Tool Parameters


Apart from running a configuration wizard, you can use the SapMaxDBBackintConfigTool tool to change a specific parameter in the veeam\_config.xml file or enable/disable Veeam Plug-In features.

|  |
| --- |
| Important |
| When you work with the command-line tool, use one configuration parameter per command. The tool does not support commands with multiple parameters. |

The following table lists available parameters for SapMaxDBBackintConfigTool.

| Parameter | Description |
| --- | --- |
| --help | Shows the list of tool parameters. |
| --show-config | Shows configuration parameters. |
| --wizard | Starts the wizard to configure the plug-in settings. The wizard edits the Veeam Plug-In configuration file (veeam\_config.xml) or creates a new one if the configuration file was removed from the /opt/veeam/VeeamPluginforSAPMaxDB directory on the machine where Veeam Plug-In is installed. |
| --set-credentials <"serv\username"> <password> | Specifies credentials to log in to the Veeam Backup & Replication server. |
| --set-host <hostname> | Specifies the IP address or hostname of the Veeam Backup & Replication server. |
| --set-port <port\_number> | Specifies a port number that will be used to communicate with the Veeam Backup & Replication server. |
| --set-repository | Launches a wizard to select a backup repository. A backup repository is selected from repositories which are available in the connected Veeam Backup & Replication instance. |
| --set-backup-for-restore | [For System Copy] Specifies the backup that will be used for restore operations. You can use this parameter if you want to restore a database to another server or to restore a database from a backup copy.  When you run the SapBackintConfigTool command with this parameter, Veeam Plug-In will prompt you to select an authentication method to access a backup created for the original server and then select the backup from which you want to restore a database.  For more information, see [Restore to Another Server](plugins_sap_maxdb_restore_to_another.md). |
| --map-backup | Maps the imported backup. |
| --set-force-delete | Deletes backup files after specified days. |
| --promote-backup-copy-to-primary | Maps the imported backup copy to a regular Veeam Plug-In backup chain. |
| --set-throttling | Specifies network traffic throttling. For more information, see [Configuring Performance Throttling](plugins_sap_maxdb_deploy_performance_throttling.md#throttle). |
| --disable-fingerprint-confirmation | Use the --disable-fingerprint-confirmation parameter only with the --set-credentials parameter.  Disables a step of the Veeam Plug-In configuration process intended to confirm the first connection to the Veeam Backup & Replication server. During this step, Veeam Plug-In provides a fingerprint for the server for the user review. |
| --show-preferred-networks | Shows the list of preferred networks set for Veeam Plug-In data traffic to the remote backup repository.  The list shows set preferred networks in descending order of priority. If the list is empty, no networks are set as preferred and Veeam Plug-In routes data traffic to the preferred networks set in Veeam Backup & Replication. For more information, see [Specifying Preferred Networks for Veeam Plug-Ins](plugins_sap_maxdb_deploy_preferred_network.md). |
| --add-preferred-network <network\_IP\_address> <position\_in\_list> | Adds a network to the list of preferred networks for Veeam Plug-In data traffic to the remote backup repository.  To select to which network Veeam Plug-In connects first, you can set the order number of the network in the list. For more information, see [Specifying Preferred Networks for Veeam Plug-Ins](plugins_sap_maxdb_deploy_preferred_network.md). |
| --remove-preferred-network <network\_IP\_address> | Removes a specified network from the list of preferred networks for Veeam Plug-In data traffic to the remote backup repository. |

Example

The following example shows how to specify credentials that will be used to log in to the Veeam Backup & Replication server.

|  |
| --- |
| SapMaxDBBackintConfigTool --set-credentials srv001\Administrator" "password" |


