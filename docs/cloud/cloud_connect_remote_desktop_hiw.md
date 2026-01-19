---
title: "How Remote Desktop Connection to Tenant Works"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_remote_desktop_hiw.html"
last_updated: "1/26/2024"
product_version: "13.0.1.1071"
---

# How Remote Desktop Connection to Tenant Works


To open and keep a remote connection to the tenant backup server over the Remote Desktop Protocol, Veeam Backup & Replication components communicate in the following way:

1. After the tenant adds the SP in their Veeam Backup & Replication console, the Veeam Backup Service running on the tenant backup server starts the Tenant network redirector.
2. The Tenant network redirector establishes the control connection to the Cloud network redirector that runs on the SP backup server waiting for connections from tenants and Remote network redirectors.
3. The Cloud network redirector accepts the control connection from the Tenant network redirector and reports information about the connected tenant to the Veeam Backup Service running on the SP backup server. The control connection remains open.
4. The Remote Access Console connects to the Veeam Backup Service running on the SP backup server and retrieves information about tenants who have opened control connections to the SP.
5. When the SP starts using the Remote Access Console to connect to the tenant backup server over the RDP protocol, the Remote Access Console starts the Remote network redirector. The Remote Access Console provides to this network redirector information about the cloud gateway and information about the tenant to whose backup server the SP is connecting.
6. The Remote Access Console starts locally the Remote Desktop Connection client (mstsc.exe) that is set up to connect to the Remote network redirector.
7. The Remote network redirector accepts connection from Remote Desktop Connection client and connects to the Cloud network redirector. The Remote network redirector provides to the Cloud network redirector information about the tenant to whose backup server the SP is connecting over the RDP protocol. After that, the Remote network redirector starts redirecting requests between the Remote Desktop Connection client and the Cloud network redirector.
8. The Cloud network redirector puts on hold the connection from the Remote Desktop Connection client and notifies the Tenant network redirector over the control connection that the Remote Access Console has requested to connect to the tenant backup server over the RDP protocol.
9. After the Tenant network redirector accepts the request over the control connection, the Tenant network redirector opens the new connection to the Cloud network redirector and provides to this network redirector information about the Remote Access Console that has requested to connect to the tenant backup server over the RDP protocol.
10. The Cloud network redirector accepts the connection from the Tenant network redirector, opens the awaiting connection from the Remote Desktop Connection client and starts redirecting requests between these connections.
11. Tenant network redirector connects to Remote Desktop Services running in the tenant backup server OS and starts redirecting requests between opened connections. The SP gains access to the tenant backup server OS over the RDP protocol.

|  |
| --- |
| Note |
| In this scenario, the Remote Access Console is deployed in the SP Veeam Cloud Connect infrastructure and communicates directly to the SP backup server. If the Remote Access Console is deployed on a remote machine in an external network, the described steps remain the same. The only difference is that the Remote Access Console will communicate to the SP backup server through the cloud gateway. |

![How Remote Desktop Connection to Tenant Works](images/remote_console_rdp_direct.webp)


