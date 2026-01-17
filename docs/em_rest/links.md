---
title: "Links"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/links.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

The main constructs of a resource representation are links. Links are the primary means to address resources and manipulate them.

When the client sends a request to the server, the server returns to the client a resource representation with a set of links. Links are elements in the XML document that the client can use to:

* Access resources to which the resource has relationships
* Perform actions with the resource
* Create new resources

Essentially, every link is a reference to another resource or some action. Links communicate to the client what the client can do next: get information about a related resource, perform some action with the resource or create a new resource, such as a new logon session.

For example, if you send an XML request to get a representation for a specific backup job resource, you will get the following set of links:

|  |
| --- |
| <Job xmlns="http://www.veeam.com/ent/v1.0" Type="Job" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5?format=Entity" Name="Exchange Backup" UID="urn:veeam:Job:568c42ce-eb11-4140-92cf-39ab36712bf5"> |

Using links from the representation of the job resource, you can get information about job sessions and the backup server on which the job was created, add objects to the job, edit the jobs settings, start, stop, retry and clone and disable/enable a job.

This resource representation contains links to the following related resources:

1. Backup server where the job is created:

|  |
| --- |
| <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/21a631e0-af7f-46ba-afbd-273de2e6fd4a" Name="localhost" /> |

1. Entity of the backup job. For details on entities, see [Resource Representation for Key Resources](resource_representation_for_ke.md).

|  |
| --- |
| <Link Rel="Alternate" Type="JobReference" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5" Name="Exchange Backup" /> |

1. List of job sessions:

|  |
| --- |
| <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5/backupSessions" /> |

The backup job resource representation also contains a set of actions that you can perform with the job resource:

1. Add VMs and VM containers to the job:

|  |
| --- |
| <Link Rel="Create" Type="ObjectInJob" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5/includes" /> |

1. Edit a job:

|  |
| --- |
| <Link Rel="Edit" Type="JobReference" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5" Name="Exchange Backup" /> |

1. Start a job:

|  |
| --- |
| <Link Rel="Start" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5?action=start" /> |

1. Stop a job:

|  |
| --- |
| <Link Rel="Stop" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5?action=stop" /> |

1. Retry a job:

|  |
| --- |
| <Link Rel="Retry" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5?action=retry" /> |

1. Clone a job:

|  |
| --- |
| <Link Rel="Clone" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5?action=clone" /> |

1. Enable or disable the job schedule:

|  |
| --- |
| <Link Rel="ToggleScheduleEnabled" Href="https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5?action=toggleScheduleEnabled" /> |

In This Section

* [Attributes of a Link Element](attributes_of_a_link_element.md)
* [Link Types and XML Schema Definition](link_types_and_xml_schema.md)

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
