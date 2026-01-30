---
title: "Step 1. Launch New Agent Backup Job Wizard"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_launch_linux.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Step 1. Launch New Agent Backup Job Wizard


You can create a Veeam Agent backup job managed by the backup server for protected computers that run a Linux OS in one of the following ways:

* [Create a new backup job](#simple) — in this case, Veeam Backup & Replication will launch the New Agent Backup Job wizard. You will be able to specify protection groups and Veeam Agent computers to which the backup job settings must apply at the [Computers](agent_job_comp_linux.md) step of the wizard.
* [Add a protection group to a new backup job](#group) — in this case, Veeam Backup & Replication will launch the New Agent Backup Job wizard and add the selected protection group to the backup job. You will also be able to change the list of Veeam Agent computers to which the backup job settings must apply at the [Computers](agent_job_comp_linux.md) step of the wizard.
* [Add individual computers to a new backup job](#computers) — in this case, Veeam Backup & Replication will launch the New Agent Backup Job wizard and add the selected computers to the backup job. You will also be able to change the list of Veeam Agent computers to which the backup job settings must apply at the [Computers](agent_job_comp_linux.md) step of the wizard.

Launching Backup Job Wizard

To launch the New Agent Backup Job wizard, do either of the following:

* On the Home tab, click Backup Job > Linux computer.
* Open the Home view. Select the Jobs node and click Backup Job > Linux computer on the ribbon.
* Open the Home view. Right-click the Jobs node and select Backup > Linux computer.

Adding Protection Group to New Backup Job

To add a protection group to a new Veeam Agent backup job, do either of the following:

* Open the Inventory view. In the Physical and Cloud Infrastructure node, right-click the protection group that you want to add to the backup job and select Add to backup job > Linux > New job.
* Open the Inventory view. In the Physical and Cloud Infrastructure node, select the protection group that you want to add to the backup job and click Add to Backup > Linux > New job on the ribbon.

Veeam Backup & Replication will start the New Agent Backup Job wizard and add the protection group to the job. You can add other protection groups and individual computers to the job later on, when you pass through the wizard steps.

Adding Computers to New Backup Job

To add specific computers to a new Veeam Agent backup job, do either of the following:

* Open the Inventory view. In the Physical and Cloud Infrastructure node, click the protection group whose computers you want to add to the backup job. In the working area, select one or more computers that you want to add to the job, right-click the selected computer and select Add to backup job > New job.
* Open the Inventory view. In the Physical and Cloud Infrastructure node, click the protection group whose computers you want to add to the backup job. In the working area, select one or more computers that you want to add to the job and click Add to Backup > New job on the ribbon.

Veeam Backup & Replication will start the New Agent Backup Job wizard and add the selected computers to the job. You can add other computers and protection groups to the job later on, when you pass through the wizard steps.

|  |
| --- |
| TIP |
| Consider the following:   * You can press and hold the [Ctrl] key to select multiple computers at once. * You can add an individual computer or protection group to a Veeam Agent backup job that is already configured in Veeam Backup & Replication. To learn more, see [Adding Computers to Backup Job](agents_protected_computers_add.md) and [Adding Protection Group to Backup Job](agents_protection_group_job.md). |

[![Launch New Agent Backup Job Wizard](images/agent_backup_job_launch_linux.webp)](images/agent_backup_job_launch_linux.webp "Launch New Agent Backup Job Wizard")


