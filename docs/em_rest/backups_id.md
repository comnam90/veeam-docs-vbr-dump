---
title: "/backups/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backups_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /backups/{ID}


Represents a backup having the specified ID. The backup is created on or imported to the backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backups/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backups/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/repositories/{ID}](repositories_id.md)
* [/restorepoints](restorepoints.md)

Methods

The following methods are supported for the /backups/{ID} resource:

[GET /backups/{ID}](get_backups_id.md)

Resource Representation

The /backups/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef UID="urn:veeam:Backup:c213fbfa-7b9e-4772-9ddc-3ecbdcc3fc70" Name="Simple backup\_1" Href="https://localhost:9398/api/backups/c213fbfa-7b9e-4772-9ddc-3ecbdcc3fc70" Type="BackupReference" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

Entity resource representation:

|  |
| --- |
| <Backup Href="http://local.host:9399/api/backups/c213fbfa-7b9e-4772-9ddc-3ecbdcc3fc70?format=Entity" Type="Backup" Name="Simple backup\_1" UID="urn:veeam:Backup:c213fbfa-7b9e-4772-9ddc-3ecbdcc3fc70" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/repositories/b8832f03-2c9e-4222-8d0b-e43e0c912f93" Name="Scale-out Backup Repository 2" Type="RepositoryReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/backups/c213fbfa-7b9e-4772-9ddc-3ecbdcc3fc70" Name="Simple backup\_1" Type="BackupReference" Rel="Alternate"/>     <Link Href="http://local.host:9399/api/backups/c213fbfa-7b9e-4772-9ddc-3ecbdcc3fc70/childbackups?format=Entity" Type="BackupList" Rel="Up"/>   </Links>   <Platform>CustomPlatform</Platform>   <BackupType>ParentBackup</BackupType> </Backup |


