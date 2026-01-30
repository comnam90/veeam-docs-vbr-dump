---
title: "Configuring Plug-In on Linux or Unix"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/configuring_rman_plugin_lin.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Configuring Plug-In on Linux or Unix


To configure Veeam Plug-In, you can use OracleRMANConfigTool. The tool configures Oracle RMAN integration settings and creates the Veeam Plug-In configuration file (veeam\_config.xml) which is stored in the /opt/veeam/VeeamPluginforOracleRMAN directory on the machine where Veeam Plug-In is installed.

Note that the Veeam Plug-In configuration tool changes the settings of Oracle RMAN. All original settings of Oracle RMAN are saved in the /opt/veeam/VeeamPluginforOracleRMAN/RMANParameters.xml file.

To configure Veeam Plug-In for Oracle RMAN, do the following:

1. Log in to the Oracle server with an account which is a member of the DBA group.
2. Launch the configuration wizard:

|  |
| --- |
| OracleRMANConfigTool --wizard |

If you have extracted files form the .TAR.GZ archive, go to the /opt/veeam/VeeamPluginforOracleRMAN folder and run the following command:

|  |
| --- |
| ./OracleRMANConfigTool --wizard |

1. Specify the DNS name or IP address of the Veeam Backup & Replication server.

|  |
| --- |
| Enter backup server name or IP address: 172.24.164.68 |

1. Specify the port which will be used to communicate with the Veeam Backup & Replication server. Default port: 10006.

|  |
| --- |
| Enter backup server port number: 10006 |

For details about other required ports, see [Ports](ports_vprman.md).

1. Specify the OS user credentials to authenticate against the Veeam Backup & Replication server.

|  |
| --- |
| Enter username: serv17\administrator  Enter password for serv17\administrator: |

|  |
| --- |
| Important |
| Consider the following:   * You can work with backups created by Veeam Plug-In only with the account used for creating the backups. If you want to use another account, assign the Veeam Backup Administrator role or Veeam Backup Operator and Veeam Restore Operator roles to the account.   For details on how to assign Veeam Backup & Replication roles, see [Managing Users and Roles](users_roles.md).   * The account must have access permissions on the required backup repository. To learn how to configure access permissions on repositories, see [Access and Encryption Settings on Repositories](repository_permissions.md). |

1. If you connect to the specified Veeam Backup & Replication server for the first time, provide the following confirmations:

1. Review the Veeam Backup & Replication server fingerprint and press y to confirm the connection to the specified server.

|  |
| --- |
| Veeam Backup & Replication server fingerprint: XX986XX6X6106XXXXX765X574X72X5X11502XXX8 |

1. Review requirements for the credentials and press y to confirm the connection using the specified credentials.

|  |
| --- |
| Please ensure the following roles are assigned to the user in Users and Roles settings on the backup server: Backup Administrator, or Backup Operator and Restore Operator  Alternatively, select a backup repository that does not have existing application backups created from this server under another user account.  Proceed anyway? (y/n): |

|  |
| --- |
| Tip |
| If you want to skip this step when connecting to the Veeam Backup & Replication server for the first time, you can disable it. For details, see [Configuration Tool Parameters](#disable). |

1. Select the backup repository where you want to store the backups. In the wizard dialog, enter the number of the repository from the list of available repositories. If you want to add several repositories, enter the required numbers separated by blank spaces.

If you want to use the Oracle RMAN Backup Duplexing functionality, you can select up to four repositories. The copies of backups will be sent to all selected repositories. Note that Oracle Database Standard Edition does not allow using more than one RMAN channel. Thus, if you use Standard Edition, you can select only one repository.

|  |
| --- |
| Available repositories are:  1. serv10\_repo  2. serv02\_repo  Specify up to 4 Veeam repositories to use as target using whitespace as a separator: 2 |

|  |
| --- |
| Important |
| The account must have access to back up repositories that you plan to use. Otherwise, the repositories will not be listed as available. To learn how to configure access permissions on repositories, see [Access and Encryption Settings on Repositories](repository_permissions.md). |

1. Specify the number of parallel data streams for each backup repository. Note that Oracle Database Standard Edition does not allow using more than one RMAN channel. Thus, if you use Standard Edition, you can select only one data stream.

|  |
| --- |
| Enter the number of data streams (From 1 to 254) to run in parallel for each repository (RMAN DEVICE PARALLELISM value).  Channel count per device: 4 |

1. If you want to enable Veeam compression of backup files, type y. For details, see [Data Compression and Deduplication](compression_deduplication.md).

|  |
| --- |
| Do you want to use Veeam compression (Y/n):y |

1. At the Select the Oracle environment authentication method step of the plug-in wizard, select the preferred authentication method to connect to the backup database.

You can choose between operating system authentication and database authentication methods. With the OS authentication method, you can connect to the server and database using only OS user credentials. With the database authentication method, you can connect to the server using OS user credentials and to the database using database user credentials. The OS user account must be a user on the Oracle server with the required permissions to run RMAN.

If you select the database authentication method, you must specify the database user account credentials. The OS user credentials will be applied automatically.

Note that the Veeam Plug-In configuration tool changes the settings of Oracle RMAN. All original settings of Oracle RMAN are saved in the /opt/veeam/VeeamPluginforOracleRMAN/RMANParameters.xml file.

For details, see [Authentication Against Database](rman_auth_methods.md).

* For the OS authentication method, at the Select the Oracle environment authentication method step of the wizard, select Operating system authentication. The OS user credentials will be used automatically.

|  |
| --- |
| Select the Oracle environment authentication method :  1. Operating system authentication  2. Database authentication  Enter:1 |

In the following RMAN settings section, the wizard will display a list of the RMAN settings that have been configured previously.

* For the database authentication method, at the Select the Oracle environment authentication method step of the wizard, select Database authentication.

|  |
| --- |
| Select the Oracle environment authentication method:  1. Operating system authentication  2. Database authentication  Enter:2 |

You can configure credentials for each of the target databases or one set of credentials for multiple databases. You can update all database credentials using the OracleRMANConfigTool command, if needed.

By default, the database user account must have the SYSDBA permission on the database. To learn more about Oracle permissions, see [this Oracle article](https://docs.oracle.com/database/121/ADMIN/dba.htm#ADMIN11047). With Oracle Database 12c, you can also authenticate with a user account that has the SYSBACKUP privileges. To learn more, see [Authentication Against Database](rman_auth_methods.md#consider).

* To configure credentials for each of the target databases, at the Select the preferred method to enter credentials step of the wizard, select Enter different credentials for each automatically detected database:

|  |
| --- |
| Select the preferred method to enter credentials:  0. Do not enter credentials and use already existing ones  1. Enter different credentials for each automatically detected database  2. Enter common credentials for multiple manually specified databases  Enter:1 |

Enter the individual database user account credentials. The OS user account credentials specified in [step 5](#creds) will be applied automatically.

|  |
| --- |
| Getting databases... 2 databases found  Enter username for ORCL: SYS  Enter password for user SYS in ORCL:  Enter username for ORCL2: SYSBACKUP  Enter password for user SYSBACKUP in ORCL2: |

* To configure common credentials for multiple target databases, at the Select the preferred method to enter credentials step of the wizard, select Enter common credentials for multiple manually specified databases:

|  |
| --- |
| Select the preferred method to enter credentials:  0. Do not enter credentials and use already existing ones  1. Enter different credentials for each automatically detected database  2. Enter common credentials for multiple manually specified databases  Enter:2 |

Specify all database names for which you want to use common credentials, and enter the user name and password you want to use:

|  |
| --- |
| Getting databases... 2 databases found  Specify database names: ORCL, ORCL2  Enter username: SYS  Enter password: |

1. At the Save configuration step of the plug-in wizard, you can export configuration files (the Veeam Plug-In configuration file and RMAN configuration file). You can import these configuration files to other servers to apply the same settings.

|  |
| --- |
| Save configuration?  1. Apply configuration to the Oracle environment  2. Export configuration into a file for manual setup  3. Cancel without saving  Enter:1    \*\*\* Database instance ORCL is configured \*\*\* |

|  |
| --- |
| Note |
| When you export the configuration files, Veeam Plug-In automatically enables Oracle's Controlfile Autobackup feature. This feature is required for [restoring with different settings](https://helpcenter.veeam.com/docs/vbr/explorers/rman_oracle_settings.html?ver=13) using Veeam Explorer for Oracle. |

|  |
| --- |
| Tip |
| It is recommended to save the configuration files, so that you can use it as a reference. For example, if you are planning to manually [allocate channels](rman_allocation_backup.md) for backup and restore operations, you will need the repository UUID. The RMAN configuration file (rman\_config.txt) contains an example for channel allocation definition for the target repository. You can use this statement in your backup/restore scripts. |

Configuration Tool Parameters

Apart from running a configuration wizard, you can use the OracleRMANConfigTool tool to change a specific parameter in the veeam\_config.xml file or enable/disable Veeam Plug-In features.

|  |
| --- |
| Important |
| When you work with the command-line tool, use one configuration parameter per command. The tool does not support commands with multiple parameters. |

The following table lists available parameters for OracleRMANConfigTool.

| Parameter | Description |
| --- | --- |
| --help | Shows the list of parameters of the plug-in configuration tool. |
| --show-config | Shows configuration parameters. |
| --wizard | Starts the wizard to configure the plug-in settings. The wizard edits the Veeam Plug-In configuration file (veeam\_config.xml) or creates a new one if the configuration file was removed from the /opt/veeam/VeeamPluginforOracleRMAN directory on the machine where Veeam Plug-In is installed. |
| --set-credentials <"serv\username"> <"password"> | Specifies credentials to connect to the Veeam Backup & Replication server. |
| --set-db-credentials | Specifies credentials to connect to a single database. |
| --set-host <hostname> | Specifies the host of the Veeam backup server. |
| --set-port <port\_number> | Specifies the host to connect to the Veeam Backup & Replication server. |
| --set-repositories | Launches a wizard to select a backup repository. A backup repository is selected from repositories which are available in the connected Veeam Backup & Replication instance. |
| --set-parallelism <number\_of\_channels> | Configures RMAN parallelism settings. |
| --compression <y/n> | Enables/disables Veeam proprietary feature which compresses backup files. |
| --set-throttling | Enables/disables network traffic throttling. For more information, see [Configuring Performance Throttling](plan_and_manage_performance_throttling_rman.md#throttle). |
| --map-backup | Maps the imported backups. |
| --set-force-delete | Configures the auto-deletion of backup files after specified days. |
| --promote-backup-copy-to-primary | Maps the imported backup copy to a regular Veeam Plug-In backup chain. |
| --set-auth-data-for-restore | Specifies an authentication method for database restore. Use this parameter if you want to restore a database to another server or to restore a database from a backup copy.  After you run the OracleRMANConfigTool command with this parameter, use the OracleRMANConfigTool command with the --set-backup-for-restore parameter to select a backup from which you want to restore a database. For more information, see [Restore to Another Server](restore_other_server_rman.md). |
| --get-backup-for-restore | Selects the backup for database restore. Use this parameter if you want to restore a database to another server or to restore a database from a backup copy.  You can run the OracleRMANConfigTool command with this parameter to select a backup after you have specified an authentication method to access the backup using the OracleRMANConfigTool --set-backup-for-restore command. For more information, see [Restore to Another Server](restore_other_server_rman.md). |
| --disable-fingerprint-confirmation | Use the --disable-fingerprint-confirmation parameter only with the --set-credentials parameter.  Disables a step of the Veeam Plug-In configuration process intended to confirm the first connection to the Veeam Backup & Replication server. During this step, Veeam Plug-In provides a fingerprint for the server for the user review. |
| --show-preferred-networks | Shows the list of preferred networks set for Veeam Plug-In data traffic to the remote backup repository.  The list shows set preferred networks in descending order of priority. If the list is empty, no networks are set as preferred and Veeam Plug-In routes data traffic to the preferred networks set in Veeam Backup & Replication. For more information, see [Specifying Preferred Networks for Veeam Plug-Ins](preferred_network_rman.md). |
| --add-preferred-network <network\_IP\_address> <position\_in\_list> | Adds a network to the list of preferred networks for Veeam Plug-In data traffic to the remote backup repository.  To select to which network Veeam Plug-In connects first, you can set the order number of the network in the list. For more information, see [Specifying Preferred Networks for Veeam Plug-Ins](preferred_network_rman.md). |
| --remove-preferred-network <network\_IP\_address> | Removes a specified network from the list of preferred networks for Veeam Plug-In data traffic to the remote backup repository. |

Example

To specify credentials that will be used to log in to the Veeam Backup & Replication server, use the plug-in configuration tool with the following command.

|  |
| --- |
| OracleRMANConfigTool --set-credentials 'serv04\joelle' 'password' |


