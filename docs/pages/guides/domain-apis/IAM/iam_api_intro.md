---
title: IAM Domain API
tags: [iam, api]
keywords: iam, api
last_updated: 08/12/2022
sidebar: guides_sidebar
permalink: iam_api_intro.html
folder: guides/domain-apis
topnav: topnav
---

The purpose of this API is to allow the integration between HR Core Beaufort and external Identity & Access Management systems, enabling important capabilities like the exchange of HR data, or performing searches on relevant information for the domain, like personal & contract details. Organisations will use this information to automate critical processes like creating accounts for new employees or to block/change the access for employees to application or even buildings when they are changing jobs.
The Identity & Access Management domain provides vital information because it helps organisations to protect their companies secrets and processes against unauthorised persons.

## Processes
The following processes can be supported with the domain API:
- Get all the relevant employee data for creating or updating the user credentials of an employee in the environment of a customer
- Get all the relevant employee data for creating or updating user specific permissions in the environment of a customer
- Get the organisation structure for managing the required approval for specific permissions
- Link the user credentials of an employee to the user in the Youforce portal


## Domain model
With different endpoint, the IAM API will support the following domain model

{% include image.html file="IAM Domainmodel.png" url="IAM Domainmodel.png" alt="IAM Domain model " %}
