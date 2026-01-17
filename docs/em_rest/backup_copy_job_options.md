---
title: "Backup Copy Job Options"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backup_copy_job_options.html"
last_updated: "8/14/2025"
product_version: "13.0.1.1071"
---


In this article

Backup copy jobs contain one of the following elements in JobInfo:

* BackupCopyJobInfo — for periodic backup copy jobs created with Veeam Backup & Replication 11a or earlier
* ImmediateBackupCopyJobInfo —  for all immediate backup copy jobs as well as periodic backup copy jobs created with Veeam Backup & Replication 12 or later

For details on the JobInfo element, see [Job Info](jobinfo.md).

The BackupCopyJobInfo and ImmediateBackupCopyJobInfo elements, in turn, contain the following settings:

* Linked jobs
* Linked backups
* Linked repositories

Linked Jobs

Linked jobs are specified in the LinkedJobIncludes object. The element represents a collection of LinkedJob objects, each of which contains the following elements.

| Element | Type | Description |
| --- | --- | --- |
| ObjectInJobId | String | Object-in-job ID assigned to the linked backup job, for example: e310aa12-eff2-41f4-97c8-631b677fc17f. |
| LinkedJobUid | String | UID of the linked backup job, for example: urn:veeam:Job:c72ec878-c0b9-44f9-8376-7f4c9a9de056. |

For example:

|  |
| --- |
| <LinkedJobResourceObjects xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://www.veeam.com/ent/v1.0"> |

Linked Backups

Linked backups are specified in the LinkedBackupIncludes object. The element represents a collection of LinkedBackup objects, each of which contains the following elements.

| Element | Type | Description |
| --- | --- | --- |
| ObjectInJobId | String | Object-in-job ID assigned to the linked backup, for example: ca8f8d69-578e-48f7-91da-81f619767984. |
| LinkedBackupUid | String | UID of the linked backup, for example: urn:veeam:Backup:58c917c7-7b7a-41ff-8676-226656c35c05. |

Linked Backup Repositories

Linked backup repositories are specified in the LinkedBackupRepositoryIncludes object. The element represents a collection of LinkedBackupRepository objects, each of which contains the following elements.

| Element | Type | Description |
| --- | --- | --- |
| ObjectInJobId | String | Object-in-job ID assigned to the linked backup repository, for example: e310aa12-eff2-41f4-97c8-631b677fc17f. |
| LinkedBackupRepositoryUid | String | UID of the linked backup repository, for example: urn:veeam:Repository:5ef453b0-f3c3-4fe7-be52-2106b6d79ca6. |

For example:

XML Representation

|  |
| --- |
| <LinkedBackupRepositoryResourceObjects xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://www.veeam.com/ent/v1.0">     <LinkedBackupRepository Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b/linkedBackupRepositories/961c9350-dc5a-43d6-8efa-867995e9404e" Type="LinkedBackupRepositoryObject">         <Links>             <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b?format=Entity" Name="Periodic Backup Copy Job" Type="Job" Rel="Up" />             <Link Href="https://enterpriseem01.tech.local:9398/api/jobs/0f5afb99-7468-42c4-a45d-28e98bc6122b/linkedBackupRepositories/961c9350-dc5a-43d6-8efa-867995e9404e" Rel="Delete" />         </Links>         <ObjectInJobId>961c9350-dc5a-43d6-8efa-867995e9404e</ObjectInJobId>         <LinkedBackupRepositoryUid>urn:veeam:Repository:da49abfc-838a-40a1-90a3-40acd2bc7000</LinkedBackupRepositoryUid>     </LinkedBackupRepository> </LinkedBackupRepositoryResourceObjects> |

Page updated 8/14/2025

Page content applies to build 13.0.1.1071
