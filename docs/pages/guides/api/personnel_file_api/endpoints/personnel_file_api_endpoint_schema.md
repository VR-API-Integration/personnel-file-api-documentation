---
title: Personnel File API Endpoint - Schema
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-07-26
sidebar: guides_sidebar
permalink: personnel_file_api_endpoint_schema.html
folder: guides/api/personnel_file_api/endpoints
topnav: topnav
---
The Schema endpoints provide metadata of the relevant entities used in the API.

<h2>GET /v10/schema/categories</h2>
<p>This API endpoint provides all document types associated with the designated tenant. The list contains document type codes and document type titles, which can be used to populate a picklist in the client application. The document type code is mandatory when adding a document to the personnel file of an employee.</p>

<h2>GET /v10/schema/category/{id}</h2>
<p>With this API endpoint you can retrieve the document type title using the unique document type code {id}. </p>

<h2>GET /v10/schema/folders</h2>
<p>This API endpoint provides the folder structure as defined in the Personnel File configuration, containing the folder titles and the document type codes of the document types in each folder. Use /v10/schema/categories to retrieve the document type titles when relevant.</p>

<h2>GET /v10/schema/employee</h2>
<p>This API endpoint provides a list of all employee properties inclusing the title, possible values, data type and maximum length. All properties are currently fixed.</p>

<h2>GET /v.0/schema/document</h2>
<p>This API endpoint provides a list of all document properties inclusing the title, possible values, data type and maximum length. All properties are currently fixed except for custom1, custom2 and custom3, which have tenant specific titles and meaning.</p>
 
