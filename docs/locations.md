---
title: "Managing Locations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/locations.html"
last_updated: "9/23/2025"
product_version: "13.0.1.1071"
---

# Managing Locations

In this article

To control data migration in the virtual infrastructure, Veeam Backup & Replication introduces a notion of location. A location defines a geographic region, or country, in which an infrastructure object resides. You can create a list of locations, and assign to backup infrastructure objects information about locations to which they belong.

Veeam Backup & Replication allows you to assign information about locations to the following infrastructure objects:

* Virtual infrastructure objects: vCenter Servers, datacenters, SCVMM, clusters and hosts.
* Backup infrastructure objects: backup repositories, scale-out backup repositories, tape libraries and tape vaults. Locations of external repositories are determined and assigned automatically based on the datacenter region.
* Agent management objects: protection groups.
* Veeam Cloud Connect for service providers: cloud repositories and hardware plans.

Information about infrastructure objects location is stored in the Veeam Backup & Replication configuration database. When VM data in the virtual infrastructure is migrated from one location to another, Veeam Backup & Replication displays a warning and stores a record about data migration to job or task session details. In addition to it, Veeam Backup & Replication logs this information to Microsoft Windows event logs. For example, if you back up VMs from a host that resides in Germany to a backup repository that resides in Australia, Veeam Backup & Replication will display a warning that VM data changes its location in the backup job wizard, display information about data migration in the backup job session details and log it to Microsoft Windows event logs.

Veeam Backup & Replication displays information about VM and file share data migration in statistics for the following types of jobs:

* Backup jobs — Veeam Backup & Replication compares the location of the source host on which VMs are registered with the location of the target backup repository or cloud repository.
* Backup copy jobs — Veeam Backup & Replication compares the location of the source host with the location of the target host.
* File backup jobs — Veeam Backup & Replication compares the location of the source file share with the location of the target backup repository or cloud repository. If the secondary repository is specified, Veeam Backup & Replication compares the location of the source file share with the location of the secondary target host.
* VeeamZIP tasks (except the cases when you select to store the VeeamZIP file in a local or shared folder) — Veeam Backup & Replication compares the location of the source host on which VMs are registered with the location of the target backup repository.
* Replication jobs — Veeam Backup & Replication compares the location of the source host on which VMs are registered with the location of the target host.
* Replica failback tasks — Veeam Backup & Replication compares the location of the source host with the location of the host to which the VM is restored.
* VM copy jobs — Veeam Backup & Replication compares the location of the source host on which VMs are registered with the location of the target backup repository or target host.
* Quick migration tasks — Veeam Backup & Replication compares the location of the source host on which VMs are registered with the location of the target host.
* File share backup copy tasks — Veeam Backup & Replication compares the location of the source file share with the location of the target backup repository or target host.
* Entire VM restore tasks — Veeam Backup & Replication compares the location of the source host with the location of the host to which VMs are restored.
* File share data recovery tasks — Veeam Backup & Replication compares the location of the source file share with the location of the file share to which files are restored.
* External repository tasks:

+ Backup copy jobs: Veeam Backup & Replication compares the location of the source external repository with the location of the target backup repository.
+ Restore to Amazon EC2: Veeam Backup & Replication compares the geographic region of the backed-up Amazon EC2 instance with the geographic region of the target EC2 instance.
+ Restore to Microsoft Azure: Veeam Backup & Replication always displays a warning about VM data migration when restore to Microsoft Azure is performed from external repositories.

* SureBackup jobs — Veeam Backup & Replication compares the source location with the target location. The target location is always a host on which the virtual lab is registered. The source location may be one of the following:

+ If a VM is added to the application group, Veeam Backup & Replication compares the host on which the VM is registered (or was registered at the moment of backup) with the target location.
+ If a VM is added to the SureBackup job from the linked job, Veeam Backup & Replication compares the backup repository on which the backup file resides with the target location.

* Tape tasks:

+ Backup to tape jobs: In backup to tape jobs, Veeam Backup & Replication compares the location of the source job or repository with the location of the tape library in the target media pool. If the media pool spans multiple tape libraries, Veeam Backup & Replication analyzes locations of all libraries in the media pool.
+ Vaults: If a tape job exports offline backups to a vault, Veeam Backup & Replication compares the location of the source job or repository with the location of the vault. If a GFS tape job exports tapes to multiple vaults, Veeam Backup & Replication analyzes all vaults configured for target media pools of the GFS tape job.
+ Media pools: Veeam Backup & Replication compares locations of all tape libraries added to the media pool. If the media pool exports tapes to a vault, Veeam Backup & Replication analyzes all vaults configured for the media pool.

Limitations for Locations

Consider the following:

* You cannot assign or edit locations of external repositories. Veeam Backup & Replication automatically determines and sets locations for external repositories based on the datacenter region. You can check the datacenter region at the [Bucket](external_repository_details.md) step of the Edit External Repository wizard.
* For SureReplica jobs, Veeam Backup & Replication does not compare information about source and target hosts location.
* Veeam Backup & Replication does not display a warning about VM data migration for file copy jobs.

In This Section

* [Creating and Assigning Locations to Infrastructure Objects](locations_create.md)
* [Editing Locations](locations_edit.md)
* [Deleting Locations](locations_delete.md)
* [Exporting and Importing Locations List](locations_export.md)

Page updated 9/23/2025

Page content applies to build 13.0.1.1071
