---
itle: WFM Domain API
tags: [wfm, api]
keywords: wfm, api
last_updated: 08/12/2022
sidebar: guides_sidebar
permalink: wfm_api_intro.html
folder: guides/domain-apis
topnav: topnav
---

The purpose of this API is to allow the integration between HR Core Beaufort and external Workforce Management Systems, enabling important capabilities like the exchange of HR data, or performing searches on relevant information for the domain, like personal & contract details and the availlebility of their employees. Organisations will use this information for resource planning and timewriting.

The Workforce Management domain provides vital information that helps organisations to align the workschedules and capacity with the needs for their business. 

## Processes
The following processes can be supported with the domain API:
- Get all the relevant basic employee data for the planning & timewriting process
- Get the availibility (absenses) of the employee for the planning & timewriting process
- Get the organization structure for the approval within the planning and timewriting process
- Get the relevant user account of the employee to support Single Sign On
- Post worked and unworked hours for the payroll process

## Domain model
With different endpoint, the WFM API will support the following domain model

*note: not all endpoints are supported yet. See the reference page for the availleble endpoints*
{% include image.html file="wfm domainmodel.png" url="wfm Domainmodel.png" alt="WFM Domain model " %}
