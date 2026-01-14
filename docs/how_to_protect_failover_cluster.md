---
title: "How to Protect Failover Clusters"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/how_to_protect_failover_cluster.html"
last_updated: "5/23/2025"
product_version: "13.0.1.1071"
---

# How to Protect Failover Clusters

In this article

Veeam Backup & Replication lets you deploy and manage Veeam Agent for Microsoft Windows on failover clusters in your infrastructure.

This scenario describes how you can use Veeam Agent to protect failover clusters. For example, Windows File Server Failover Clusters. For the full list of failover cluster types that you can back up with Veeam Agent, see [Failover Cluster Support](agents_cluster_support.md).

|  |
| --- |
| NOTE |
| If you want to back up a a Microsoft Exchange Database Availability Group without an Administrative Access Point (IP Less DAG), follow backup job configuration procedure for standalone servers. To learn more, see [Backup of Database Availability Groups](agents_dag_hiw.md). |

In this scenario, you will:

1. [Create a failover cluster protection group](#group).
2. [Create a failover cluster backup job](#job).

To create a protection group to backup failover clusters:

1. Launch the New Protection Group wizard. Select the Microsoft Active Directory objects protection group type.

![How to Protect Failover Clusters](images/pg_add_ad.webp)

1. At the Name step of the wizard, specify a name and description for the protection group. Click Next.

![How to Protect Failover Clusters](images/clusters_protection_group_name.webp "Specify Protection Group Name")

1. At the Active Directory step of the wizard, select failover clusters that you want to add to the protection group. Click Next.

![How to Protect Failover Clusters](images/clusters_protection_group_object.webp "Select Failover Clusters to Back Up")

1. At the Exclusions step of the wizard, make sure that none of the required hosts are excluded. Click Next.

![How to Protect Failover Clusters](images/clusters_protection_group_exclusions.webp "Specify Exclusions")

1. At the Credentials step of the wizard, specify credentials to connect to each failover cluster. If you want to use the same credentials for all failover clusters, select the necessary user account from the Master account list. If some failover clusters require a different user account, specify custom credentials. Click Next.

![How to Protect Failover Clusters](images/clusters_protection_group_credentials.webp "Specify Credentials")

1. At the Options step of the wizard, specify settings for discovery and Veeam Agent deployment. Click Next.

![How to Protect Failover Clusters](images/protection_group_options.webp "Specify Discovery and Deployment Options")

1. At the Review step of the wizard, review what Veeam Backup & Replication components are already installed on the distribution server specified for the protection group and what components will be installed. Click Apply to add the configured protection group to the inventory.

![How to Protect Failover Clusters](images/clusters_protection_group_review.webp "Review Veeam Backup & Replication Components")

1. At the Apply step of the wizard, wait for the operation of the protection group creation to complete. Click Next.

![How to Protect Failover Clusters](images/clusters_protection_group_apply.webp "Apply Protection Group Settings")

1. At the Summary step of the wizard, review information about the created protection group. Click Finish to close the wizard.

![How to Protect Failover Clusters](images/clusters_protection_group_finish.webp "Save Protection Group")

To create a failover cluster backup job:

1. Select Backup Job > Windows computer to launch the New Agent Backup Job wizard.
2. At the Job Mode step of the wizard, in the Type field select Failover Cluster. Click Next.

![How to Protect Failover Clusters](images/clusters_backup_job_type.webp "Select Backup Job Type")

1. At the Name step of the wizard, specify a name and description for the backup job. Click Next.

![How to Protect Failover Clusters](images/clusters_backup_job_name.webp "Specify Backup Job Name")

1. At the Computers step of the wizard, select a protection group that contains failover clusters. Click Next.

![How to Protect Failover Clusters](images/clusters_backup_job_computers.webp "Select Objects to Back Up")

1. At the Backup Mode step of the wizard, select the mode in which you want to create a backup. Click Next.

![How to Protect Failover Clusters](images/clusters_backup_job_mode.webp "Select Backup Job Mode")

1. [For volume-level backup] At the Objects step of the wizard, specify volumes you want to include in the backup. Click Next.

![How to Protect Failover Clusters](images/agent_job_volumes.webp "Specify Backup Job Scope")

1. At the Storage step of the wizard, specify settings for the target backup repository. Click Next.

![How to Protect Failover Clusters](images/agent_job_vbr_repo.webp "Specify Backup Repository Settings")

1. [If you selected the Configure secondary destinations for this job check box at the Storage step of the wizard] At the Secondary Target step of the wizard, link the Veeam Agent backup job to a backup to tape or backup copy job. Click Next.

![How to Protect Failover Clusters](images/agent_job_secondary.webp "Specify Secondary Target")

1. At the Guest Processing step of the wizard, specify guest OS processing settings. Click Next.

![How to Protect Failover Clusters](images/clusters_backup_job_vss.webp "Specify Guest Processing Settings")

1. At the Schedule step of the wizard, specify the schedule according to which you want to perform backup. Click Apply.

![How to Protect Failover Clusters](images/agent_job_schedule_server.webp "Specify Backup Job Schedule")

1. At the Summary step of the wizard, review settings of the configured backup job. Click Finish to close the wizard.

![How to Protect Failover Clusters](images/clusters_backup_job_summary.webp "Save Backup Job")

Page updated 5/23/2025

Page content applies to build 13.0.1.1071
