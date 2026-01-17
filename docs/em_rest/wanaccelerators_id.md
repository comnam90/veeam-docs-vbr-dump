---
title: "/wanAccelerators/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/wanaccelerators_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /wanAccelerators/{ID}


Represents a WAN accelerator having the specified ID.

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/wanAccelerators/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/wanAccelerators/{ID}?format=Entity |

Related Resources

* [/backupServers](backupservers.md)
* [/wanAccelerators](wanaccelerators.md)

Methods

The following methods are supported for the /wanAccelerators/{ID} resource:

[GET /wanAccelerators/{ID}](get_wanaccelerators_id.md)

Resource Representation

The /wanAccelerators/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="WanAcceleratorReference" Href="https://localhost:9398/api/wanAccelerators/55bd11af-696d-4224-ae9c-0917c851177c" Name="172.16.13.45" UID="urn:veeam:WanAccelerator:55bd11af-696d-4224-ae9c-0917c851177c"> |

Entity resource representation:

|  |
| --- |
| <WanAccelerator xmlns="http://www.veeam.com/ent/v1.0" Type="WanAccelerator" Href="https://localhost:9398/api/wanAccelerators/55bd11af-696d-4224-ae9c-0917c851177c?format=Entity" Name="172.16.13.45" UID="urn:veeam:WanAccelerator:55bd11af-696d-4224-ae9c-0917c851177c">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Alternate" Type="WanAcceleratorReference" Href="https://localhost:9398/api/wanAccelerators/55bd11af-696d-4224-ae9c-0917c851177c" Name="172.16.13.45" />   </Links>   <Description>WAN Accelerator in Columbus</Description>   <OutOfDate>false</OutOfDate>   <Version>8.0</Version>   <Capacity>100</Capacity>   <TrafficPort>6165</TrafficPort>   <ConnectionsCount>5</ConnectionsCount>   <CachePath>C:\VeeamWAN</CachePath>   <HighBandwidthModeEnabled>false</HighBandwidthModeEnabled> </WanAccelerator> |


