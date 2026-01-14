---
title: "cloud_connect_gateways"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_gateways.html"
last_updated: "9/29/2025"
product_version: "13.0.1.1071"
---


In this article

The procedure of cloud gateway configuration is performed by the SP on the SP Veeam backup server.

When you configure the Veeam Cloud Connect infrastructure, you must deploy at least one cloud gateway. Cloud gateways are network appliances that route traffic between tenants’ Veeam backup servers and SP cloud infrastructure components. The role of a cloud gateway can be assigned to any Microsoft Windows server or Linux server, including the Veeam backup server.

You can deploy one or several cloud gateways. Several cloud gateways can be set up for scalability purposes, to balance the traffic load in the Veeam Cloud Connect infrastructure.

Before deploying a cloud gateway, [check prerequisites](cloud_connect_gateway_before_you_begin.md). Then use the New Cloud Gateway wizard to add a cloud gateway.

1. [Launch the New Gateway wizard](cloud_connect_gateway_launch.md).
2. [Choose a server](cloud_connect_gateway_server.md).
3. [Specify network settings](cloud_connect_gateway_settings.md).
4. [Review cloud gateway settings](cloud_connect_gateway_review.md).
5. [Assess results](cloud_connect_assess_results.md).
6. [Finish working with the wizard](cloud_connect_gateway_finish.md).

Related Concepts

[Cloud Gateway](cloud_connect_gateway.md)

Page updated 9/29/2025

Page content applies to build 13.0.1.1071
