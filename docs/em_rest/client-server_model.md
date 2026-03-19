---
title: "Client-Server Model"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/client-server_model.html"
last_updated: "3/18/2026"
product_version: "13.0.1.2067"
---

# Client-Server Model


The REST API relies on the client-server model:

1. The client makes requests to the Veeam Backup Enterprise Manager server over the HTTPS protocol.
2. The server processes the request and returns either a success status or an error. If the request is successful, the server returns a response body in the XML or JSON format.
3. The client receives the response, parses it and retrieves the required information.

![Client-Server Model](images/client-server.webp "Client-Server Model")


