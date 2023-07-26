---
title: Introduction
tags: [dossier, api]
keywords: dossier, api
last_updated: 2023-07-26
sidebar: guides_sidebar
permalink: dossier_api_intro.html
folder: guides/api
topnav: topnav
---

<span class="label label-success">GENERAL AVAILABLE</span>

The purpose of this API is to allow the integration between an external system providing documents for storage in the personnel file of an employee in Personnel File of Youforce or YouServe. The API provides functions to retrieve (filtered) list of employees/employments, a list of available document types stems and to add a document to the personnel file of a specific employee. 
Organisations can use this API to automate the storage of a new document in Personnel File from an external system like a Multi-Functional Printer (MFP), a scanner, workflow systems or other software that produce documents.

## Processes
The following processes can be supported with the domain API:
- Get all the relevant employee data for selecting an employee/employments from a list
- Get the available document types for selecting a document type from a list
- Get all the relevant employee data and document type for adding a new  document


## Domain model
The Dossier API will support the following domain model

{% include image.html file="dossier_api_domain_model.png" alt="Dossier API Domain Model " %}

