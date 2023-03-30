---
title: MLM API
tags: [mlm, api]
keywords: mlm, api
last_updated: 30/03/2023
sidebar: guides_sidebar
permalink: mlm_api_intro.html
folder: guides/domain-apis
topnav: topnav
---
<span class="label label-danger">CONTROLLED AVAILABLE</span>



The purpose of this API is to allow the integration between HR Core Beaufort and  Medical Leave Managment systems. The API supports the master data for Medical Leave Management Systems and can be used together with the Sivi messages system.
The basis HR data will contain only the employee and organisation data. For adding the sickness and maternity information the Sivi solution is availleble.

The Medical Leave Managment domain provides the basic HR information that helps organisation and employees in prevending sickness by a request for a consult with the company doctor without a sickness case. 
Note: for sickness employees the Sivi messages is needed.

## Processes
The following processes can be supported with the domain API:
- Get all the relevant basic employee data, so the employee can request for a consult with the company doctor

## Domain model
With different endpoint, the MLM api will support the following domain model

{% include image.html "/youforce-api-documentation/pages/guides/domain-apis/MLM/mlm domainmodel.png" alt="MLM Domain model " %}
