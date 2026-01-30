---
title: "Configuration Commands"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_configure_commands.html"
last_updated: "8/28/2025"
product_version: "13.0.1.1071"
---

# Configuration Commands


You can use the DB2ConfigTool tool to change specific parameters in the configuration file, located in the /opt/veeam/VeeamPluginforDB2 directory.

|  |
| --- |
| Important |
| When you work with the command-line tool, use one configuration parameter per command. The tool does not support commands with multiple parameters. |

You can use the following parameters with DB2ConfigTool:

| Parameter | Description |
| --- | --- |
| --help | Shows the list of tool parameters. |
| --show-config | Shows configuration parameters. |
| --wizard | Starts the wizard to configure the plug-in settings. This wizard edits the Veeam Plug-In configuration file (veeam\_config.xml) or creates a new one if the configuration file was removed from the /opt/veeam/VeeamPluginforDB2 directory on the machine where Veeam Plug-In is installed. |
| --set-credentials <"serv\username"> <password> | Specifies credentials to log in to the Veeam Backup & Replication server. |
| --set-host <hostname> | Specifies the IP address or hostname of the Veeam Backup & Replication server. |
| --set-port <port\_number> | Specifies a port number that Veeam Plug-In will use to communicate with the Veeam Backup & Replication server. |
| --set-repository | Launches a wizard to select a backup repository. A backup repository is selected from repositories which are available in the connected Veeam Backup & Replication server. |
| --compression | Sets Veeam Plug-In to use built-in compression functionality of Veeam Backup & Replication. |
| --set-throttling | Sets Veeam Plug-In to limit network bandwidth consumption. For details, see [Configuring Performance Throttling](db2_plan_and_manage_performance_throttling.md#throttle). |
| --set-logarchmeth | Sets Veeam Plug-In to use logarchmeth1 configuration parameter. For details, see [this IBM article](https://www.ibm.com/docs/en/db2/11.5?topic=parameters-logarchmeth1-primary-log-archive-method). |
| --map-backup | Maps the imported backups. For details, see [Importing Backup Files](db2_import_backup.md). |
| --get-restore-points | Returns a list of backups of your machine which are available in the connected Veeam Backup & Replication server.  To run the DB2ConfigTool command with this parameter, you must also specify the --time-range parameter with value in the yyyymm format. For details, see [Get Backup Time Stamp](db2_restore_get_time_stamp.md). |
| --set-force-delete | Deletes backup files after specified days. |
| --promote-backup-copy-to-primary | Maps the imported backup copy to a regular Veeam Plug-In backup chain. |
| --set-backup-for-restore | [For System Copy] Specifies the backup that will be used for restore operations. You can use this parameter if you want to restore a database to another server or to restore a database from a backup copy.  When you run the DB2ConfigTool command with this parameter, Veeam Plug-In will prompt you to select an authentication method to access a backup created for the original server and then select the backup from which you want to restore a database. For details, see [Restore to Another Server](db2_restore_to_another.md). |
| --disable-fingerprint-confirmation | Use the --disable-fingerprint-confirmation parameter only with the --set-credentials parameter.  Disables a step of the Veeam Plug-In configuration process intended to confirm the first connection to the Veeam Backup & Replication server. During this step, Veeam Plug-In provides a fingerprint for the server for the user review. |
| --show-preferred-networks | Shows the list of preferred networks set for Veeam Plug-In data traffic to the remote backup repository.  The list shows set preferred networks in descending order of priority. If the list is empty, no networks are set as preferred and Veeam Plug-In routes data traffic to the preferred networks set in Veeam Backup & Replication. For more information, see [Specifying Preferred Networks for Veeam Plug-Ins](db2_preferred_network.md). |
| --add-preferred-network <network\_IP\_address> <position\_in\_list> | Adds a network to the list of preferred networks for Veeam Plug-In data traffic to the remote backup repository.  To select to which network Veeam Plug-In connects first, you can set the order number of the network in the list. For more information, see [Specifying Preferred Networks for Veeam Plug-Ins](db2_preferred_network.md). |
| --remove-preferred-network <network\_IP\_address> | Removes a specified network from the list of preferred networks for Veeam Plug-In data traffic to the remote backup repository. |

Example

To specify credentials that will be used to log in to the Veeam Backup & Replication server, use the plug-in configuration tool with the following command:

|  |
| --- |
| DB2ConfigTool --set-credentials "serv02\Administrator" password |


