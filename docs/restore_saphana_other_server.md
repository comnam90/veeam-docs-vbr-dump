---
title: "Restore to Another Server (System Copy)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_saphana_other_server.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# Restore to Another Server (System Copy)


You can restore SAP HANA databases from Veeam Plug-In backups to another server. To restore databases to another server, you must specify an authentication method to access the backup created for the original server and then select the backup from which you want to restore a database.

Veeam Plug-In supports the following authentication methods to access backups:

* Using credentials of the account under which the backup was created. This option is intended for backups created using SAP HANA backup tools on the SAP HANA server.
* Using a security certificate. This option is intended for backups created using an application backup policy configured in Veeam Backup & Replication.
* Using a recovery token. This option is intended for backups created using an application backup policy configured in Veeam Backup & Replication. To use this option, a backup administrator or a restore operator must create a recovery token for the backup in Veeam Backup & Replication.

You can select the authentication method explicitly or choose to use the same method that was specified during the Veeam Plug-In configuration process.

Consider the following:

* For restore to another server, you can use either backups or backup copies of SAP HANA databases.
* If you perform restore from a backup that was imported to Veeam Backup & Replication, Veeam Plug-In will automatically create the backup job in Veeam Backup & Replication.
* During the restore process, backup operations are not disabled on the SAP HANA server.

|  |
| --- |
| Note |
| If you perform a system copy from another database to a database that was previously backed up by Veeam Plug-In, consider the following:   * If the [catalog\_backup\_using\_backint](sap_environment_saphana.md#vsph-backup-backint) parameter is enabled, after performing a system copy, SAP HANA automatically starts a new log chain and sends it to the backint along with a new catalog backup. This new catalog backup overwrites the previous catalog, making it impossible to access pre-restore backups for this database. * If you plan to restore the older state of this database, you can disable the [catalog\_backup\_using\_backint](sap_environment_saphana.md#vsph-backup-backint) parameter before performing the system copy. * Also, to have access to pre-restore backups, you can store a copy of the old backup catalog outside the default directory and specify this catalog during the restore. |

Restore to Another Server Using Configured Authentication

You can restore a database to another server using an account and authentication method that were specified in the Veeam Plug-In settings during the Veeam Plug-In configuration process. To do this, do the following:

1. Go to /opt/veeam/VeeamPluginforSAPHANA and run the following command:

|  |
| --- |
| VM2ADM:/opt/veeam/VeeamPluginforSAPHANA> SapBackintConfigTool --set-backup-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using the authentication method that was specified during the Veeam Plug-In configuration process, type 1:

|  |
| --- |
| Select authentication type or disable the functionality: |

1. Veeam Plug-In will display backups available for restore under the user account specified in the Veeam Plug-In configuration. The list of backups depends on the authentication method specified for the user account:

* For the user account with a security certificate, Veeam Plug-In displays backups created under this user account.
* For the user account with credentials, if the account has the Veeam Restore Operator role assigned in Veeam Backup & Replication, Veeam Plug-In displays all backups that reside in the backup repository. Otherwise, Veeam Plug-In displays backups created under the specified user account.
* For the user account with a recovery token, Veeam Plug-In displays backups for which the recovery token was generated.

|  |
| --- |
| Note |
| Keep in mind that Veeam Plug-In will list only those backups that were made on machines with the same architecture as the machine you are working on.  For example, if your machine has a x86\_64 architecture, only backups made on machines with the x86\_64 architecture will be displayed. |

Select a backup to start the restore process:

|  |
| --- |
| Select backup to be used: 1. Backup1 2. Backup2 3. Backup3 Enter backup number: 3 The selected backup [Backup3] will be used for all restore operations. |

1. Perform the SAP HANA System Copy based restore following [this SAP KB article](https://apps.support.sap.com/sap/support/knowledge/preview/en/2486224) (requires an SAP ID).

Restore to Another Server Using Credentials

To restore a database to another server, you can specify credentials of a user account under which the backup was created. To do this, do the following:

1. Go to /opt/veeam/VeeamPluginforSAPHANA and run the following command:

|  |
| --- |
| SapBackintConfigTool --set-backup-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using credentials of the account under which the backup was created, type 2:

|  |
| --- |
| Select authentication type or disable the functionality: 0. To disable the functionality 1. Currently set authentication data 2. Credentials 3. Recovery token Enter authentication type number: 2 |

1. Veeam Plug-In will prompt you to provide credentials of the user account that under which the backup was created. Enter a user name and password of the account:

|  |
| --- |
| Enter username: Enter password for <username>: |

1. Veeam Plug-In will display backups available for restore under the specified user account. If the account has the Veeam Restore Operator role assigned in Veeam Backup & Replication, Veeam Plug-In displays all backups that reside in the backup repository. Otherwise, Veeam Plug-In displays backups created under the specified user account.

Select a backup to start the restore process:

|  |
| --- |
| Select backup to be used: 1. Backup1 2. Backup2 3. Backup3 Enter backup number: 3 The selected backup [Backup3] will be used for all restore operations. |

1. Perform the SAP HANA System Copy based restore following [this SAP KB article](https://apps.support.sap.com/sap/support/knowledge/preview/en/2486224) (requires an SAP ID).

Restore to Another Server Using Recovery Token

You can restore a database to another server using a recovery token generated in Veeam Backup & Replication and provided to you by a backup administrator or by a restore operator. To do this, do the following:

1. Go to /opt/veeam/VeeamPluginforSAPHANA and run the following command:

|  |
| --- |
| VM2ADM:/opt/veeam/VeeamPluginforSAPHANA> SapBackintConfigTool --set-backup-for-restore |

1. Veeam Plug-In will prompt you to select an authentication method to access the backup. To access the backup using a recovery token, type 3:

|  |
| --- |
| Select authentication type or disable the functionality: 0. To disable the functionality 1. Currently set authentication data 2. Credentials 3. Recovery token Enter authentication type number: 3 |

1. Veeam Plug-In will display the fingerprint of the Veeam Backup & Replication server and prompt you to provide a recovery token:

|  |
| --- |
| Veeam Backup & Replication server fingerprint: CA4F820F164C02A9AAC75562FC35330A93CDAA3C. Continue? (y/n) : y Enter recovery token: |

1. Veeam Plug-In will display backups for which the recovery token was generated. Select the necessary backup:

|  |
| --- |
| Select backup to be used: 1. Backup1 2. Backup2 3. Backup3 Enter backup number: 3 The selected backup [Backup3] will be used for all restore operations. |

1. Perform the SAP HANA System Copy based restore following [this SAP KB article](https://apps.support.sap.com/sap/support/knowledge/preview/en/2486224) (requires an SAP ID).


