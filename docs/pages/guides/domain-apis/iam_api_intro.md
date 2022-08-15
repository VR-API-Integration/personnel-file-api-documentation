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

The domain model for Identity & Access Management contains all common and relevant HR data needed for Identity & Access Management systems who are responsible for creating accounts and permissions in different systems. 

## Processes
The following processes can be supported with the domain API:
- Get all the relevant employee data for creating or updating the user credentials of an employee in the environment of a customer
- Get all the relevant employee data for creating or updating user specific permissions in the environment of a customer
- Get the organisation structure for managing the required approval for specific permissions
- Link the user credentials of an employee to the user in the Youforce portal


## Domain model 
The domain model contains the following entities:

{% include image.html file="IAM Domainmodel.png" url="/images/IAM Domainmodel.png" alt="IAM Domain model " %}