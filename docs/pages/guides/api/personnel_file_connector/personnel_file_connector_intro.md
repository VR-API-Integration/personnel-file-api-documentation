---
title: Personnel File Connector - Introduction
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-07-26
sidebar: guides_sidebar
permalink: personnel_file_connector_intro.html
folder: guides/api/personnel_file_connector
topnav: topnav
---

<span class="label label-success">CONCEPT</span>

The purpose of the Personnel File Connector API is to connect an external system, which generates documents for employees, with the Youforce or YouServe Personnel File. It provides functions to retrieve filtered lists of employees, retrieve available document types, and adding documents to a specific employee's personnel file. Organizations can use this API to automate the storage of new documents from external sources like MFPs, scanners, or workflow systems directly into the employees' Personnel Files.

## Processes
The following processes can be supported with the Personnel File Connector:

- Get a list of document types with document type codes and document type titles
- Get the title of a document type
- Get a list of folders with the document types per folder
- Get a list of available properties of employees and employments
- Get a list of available properties of documents
- Get a filtered list maximized to 1.000 hits of employees and employments with all relevant properties using filter expressions
- Get the properties of a specific employee using the employeenumber
- Add a document with required and optional properties using multipart/form-data
- Add a document with required and optional properties using multipart/mixed
- Add a document with required and optional properties using application/json

## Domain model
The Personnel File Connector will support the following domain model

{% include image.html file="personnel_file_connector_domain_model.png" width="50%" height="50%" alt="Personnel File Connector Domain Model" %}
