---
title: "Step 4. Select Computers to Back Up"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_comp_linux.html"
last_updated: "9/1/2025"
product_version: "13.0.1.1071"
---

# Step 4. Select Computers to Back Up

In this article

At the Computers step of the wizard, select protection groups and individual computers that you want to back up with the Veeam Agent backup job managed by the backup server.

You can add to the backup job one or more protection groups and individual computers from the Veeam Backup & Replication inventory. You can also add to the job computers that are not added to inventory yet. Veeam Backup & Replication will add such computers to the job and also add them to the Manually Added protection group.

If Veeam Backup & Replication discovers a new computer in a protection group after the Veeam Agent backup job is created, Veeam Backup & Replication will automatically update the job settings to include the added computer.

|  |
| --- |
| NOTE |
| * Veeam Backup & Replication displays protection groups for pre-installed Veeam Agents and their members only if you selected the Managed by Agent option at the Job Mode step of the wizard. You cannot add protection groups for pre-installed Veeam Agents to backup jobs managed by backup server. To learn more, see [Selecting Job Mode](agent_job_protection_linux.md#mode). * If you used the Add to backup job > Linux > New job option to launch the New Agent Backup Job wizard, the Protected computers list will already contain computers that you have selected to add to the job. You can remove some computers from the job or add new computers to the job, if necessary. |

Adding Protection Groups and Computers from Inventory

To add protection groups and individual computers to the Veeam Agent backup job, do the following:

1. Click Add > Protection group.
2. In the Select Objects window, select one or more protection groups and computers in the list and click OK. You can press and hold the [Ctrl] or [Shift] key to select multiple objects at once.

To quickly find the necessary object, use the search field at the bottom of the Select Objects window.

1. Enter the object name or a part of it in the search field.
2. Click the Start search button on the right or press [Enter].

![Step 4. Select Computers to Back Up](images/agent_job_computers_linux.webp)

Adding New Computers

To add to the Veeam Agent backup job managed by the backup server new computers that do not exist in the inventory, do the following:

1. Click Add > Individual computer.
2. In the Add Computer window, in the Host name or IP address field, enter a full DNS name or hostname of the computer that you want to add to the job.
3. Select a method to connect to the computer:

* Connect using admin credentials. In this case, from the Credentials list, select a user account that has administrative permissions on the computer that you want to add to the protection group. Veeam Backup & Replication will use this account to connect to the protected computer and perform the necessary operations on the computer: upload and install Veeam Agent, and so on.

If you have not set up credentials beforehand, click the Manage accounts link or click Add on the right to add credentials.

Veeam Backup & Replication allows to add the following types of credentials:

* Stored credentials. Select stored credentials if you want Veeam Backup & Replication to use the specified user name and password for each connection to Veeam Agent.
* Single-use credentials. Select single-use credentials if you do not want Veeam Backup & Replication to store credentials in the configuration database. With this option selected, Veeam Backup & Replication will use the specified user name and password only for the first connection to Veeam Agent. After that, Veeam Backup & Replication will use Veeam Transport Service to communicate with the Veeam Agent computer.

* Connect using certificate-based authentication. Select this option, if you chose to pre-install Veeam Deployer Service on the Linux computer that you want to add to the backup job. In this case, Veeam Backup & Replication will communicate with the Linux computer using a certificate. To learn more, see [Deploying Veeam Agent Using Veeam Deployment Kit](agents_deploy_deployer.md).

![Step 4. Select Computers to Back Up](images/agent_job_computer_linux.webp)

Page updated 9/1/2025

Page content applies to build 13.0.1.1071
