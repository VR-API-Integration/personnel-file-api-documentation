---
title: Personnel File API - Introduction
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-07-26
sidebar: guides_sidebar
permalink: personnel_file_api_intro.html
folder: guides/api/personnel_file_api
topnav: topnav
---

<span class="label label-success">CONCEPT</span>

The purpose of the Personnel File API is to connect an external system, which generates documents for employees, with the Youforce or YouServe Personnel File. It provides functions to retrieve filtered lists of employees, retrieve available document types, and adding documents to a specific employee's personnel file. Organizations can use this API to automate the storage of new documents from external sources like MFPs, scanners, or workflow systems directly into the employees' Personnel Files.

## Workflow
To be able to send a document to Personnel File, a number of document properties have to be provided next to the actual document. The most import ones are the employee (employee number) and the document type (category code). Additionaly a number of mandatory properties are required, such as the start date, the description and the content type. To be able to determine how a document was added to Personnel File, the source system, source module and source identifier are also mandatory.

Except for the employee and the document type, all properties are determined by the client application that is using the API. To determine the employee, an API function can be used to retrieve the properties of employees. This data can be used to have a user pick an employee from a list in the client application. To determine the document type, an API function can be used to retrieve a list of document types. Additionaly the folder structure that is used in Personnel File can be retrieved to show a similar structure in the cleint application that is using the API.

A typical workflow is as follows:

1. Retrieve a list of employees from the API and show them in a selection list in the client application
2. Retrieve a list of document types from the API and show them in a selection list in the client application
3. Let the user enter the values of necessary properties needed to send a document to Personnel File
4. Send a document to the API using the employee number of the selected employee, the category code of the selected document and the values entered by the user of the client application

Each of these steps can be enhanced further by providing more options in the client application, such as retrieving a filtered list based on selection criteria entered by the user or showing the available documenttypes in a folder structure instead of a plain list. Also a document can be linked to an employee only, or to a specific employment of the employee. When a document is also linked to an employment, only users of Personnel File with authorization for that employment can view the document.

## Processes
The following processes can be supported with the Personnel File API:

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
The Personnel File API will support the following domain model

{% include image.html file="personnel_file_api_domain_model.png" width="50%" height="50%" alt="Personnel File API Domain Model" %}
