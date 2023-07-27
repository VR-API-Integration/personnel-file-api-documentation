---
title: Introduction
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-07-26
sidebar: guides_sidebar
permalink: personnel_file_connector_intro.html
folder: guides/api/personnel_file_connector
topnav: topnav
---

<span class="label label-success">CONCEPT</span>

The purpose of this API is to connect an external system, which generates documents for employees, with the Youforce or YouServe Personnel File. It provides functions to retrieve filtered lists of employees, retrieve available document types, and adding documents to a specific employee's personnel file. Organizations can use this API to automate the storage of new documents from external sources like MFPs, scanners, or workflow systems directly into the employees' Personnel Files.

## Processes
The following processes can be supported with the domain API:
- Get all the relevant employee data for selecting an employee/employments from a list
- Get the available document types for selecting a document type from a list
- Get all the relevant employee data and document type for adding a new  document


## Domain model
The Dossier API will support the following domain model

{% include image.html file="dossier_api_domain_model.png" width="50%" height="50%" alt="Dossier API Domain Model" %}