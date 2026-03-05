---
title: "Backup Target"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_backup_target.html"
last_updated: "2/24/2026"
product_version: "13.0.1.1071"
---

# Backup Target


Backed up data can be stored in the following disk-based systems:

* Local (internal) storage of the backup repository
* Direct Attached Storage (DAS)

The DAS must be connected to the backup repository, including external USB/eSATA drives, USB pass through and raw device mapping (RDM) volumes.

* Storage Area Network (SAN)

The backup repository must be connected into the SAN fabric through hardware or virtual HBA, or software iSCSI initiator.

* Network Attached Storage (NAS)

The NAS must be able to present its capacity as NFS share (protocol versions 3.0 and 4.1 only) or SMB (CIFS) share (any protocol versions). Using SMB (CIFS) protocol for non-continuously available (CA) file shares is not recommended for reliability reasons. Using consumer-grade NAS storage without an enterprise-grade RAID controller with battery-backed write cache (BBWC) is not recommended for reliability considerations.

* Veeam Data Cloud Vault
* Amazon S3
* Google Cloud Storage
* IBM Cloud Object Storage
* Microsoft Azure Blob Storage
* Wasabi Hot Cloud Storage
* 11:11 Cloud Object Storage
* Any S3-compatible object storage (on-premises appliance, or cloud storage provider)
* Dell Data Domain (DD OS version 7.9 to 8.6) with DDBoost license. Both Ethernet and Fibre Channel (FC) connectivity options are supported.
* ExaGrid1 (firmware version 7.2.0 P08 or later)
* Fujitsu ETERNUS CS8001 (CS800 software version 5.2.0 or later)
* HPE StoreOnce (firmware version 3.18.18 or later for Gen3, 4.2.3 or later for Gen4, 5.1.0 or later for Gen 5) with Catalyst license

Both Ethernet and Fibre Channel (FC) connectivity are supported. Note that HPE StoreOnce Federated Catalyst is not supported.

* Infinidat InfiniGuard1 (InfiniGuard software 3.12 or later)
* Quantum DXi1 (DXi software 5.2.0 or later)

Supported Quantum DXi systems include DXiV5000, DXi4800, DXi4801, DXi9000, DXi9100, DXi9200, DXiT10.

1 These storage systems use the Veeam Transport Service. Make sure that they also meet [system requirements for the backup repository](#repo).

Once backups are created, they can be copied (for redundancy) or offloaded (for long-term retention) to hot or cold storage classes of the following object storage systems using the [Scale-Out Backup Repository](backup_repository_sobr.md) [Capacity Tier](capacity_tier.md):

* Veeam Data Cloud Vault
* Amazon S3 (including AWS Snowball Edge)
* Google Cloud Storage
* IBM Cloud Object Storage
* Microsoft Azure Blob storage (including Microsoft Azure Data Box)
* Wasabi Hot Cloud Storage
* 11:11 Cloud Object Storage
* Any S3-compatible object storage (on-premises appliance, or cloud storage provider)

Once backups are created, they can be further offloaded to archive storage classes of the following object storage systems using the [Scale‑Out Backup Repository](backup_repository_sobr.md) [Archive Tier](archive_tier.md):

* Amazon S3 Glacier Instant Retrieval
* Amazon S3 Glacier Flexible Retrieval
* Amazon S3 Glacier Deep Archive
* Microsoft Azure Archive Tier
* Microsoft Azure Cold Tier
* Any S3-compatible object storage with data archiving enabled

For the full list of partner-tested solutions including primary backup storage solutions, S3-compatible object storage solutions and offline storage solutions, see [this Veeam page](https://www.veeam.com/ready.html).

For information on unstructured data backup target, see Storage Repositories in the [Backup Infrastructure for Unstructured Data Backup](unstructured_data_backup_infrastructure.md#backup_repository) section.


