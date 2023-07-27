---
title: Endpoint - Employees
tags: [dossier, personnel file, api, connector]
keywords: dossier, personnel file, api, connector
last_updated: 2023-07-26
sidebar: guides_sidebar
permalink: personnel_file_connector_endpoint_employee.html
folder: guides/api/personnel_file_connector/endpoints
topnav: topnav
---

GET /v1.0/employees
This API endpoint allows you to list all the employees associated with a designated tenant. By default, the endpoint will return a list of all employees in a random order. However, the endpoint also supports advanced functionality, including paging, sorting, and querying.

With paging, you can retrieve the employee list in smaller, more manageable chunks. With sorting, you can arrange the employee list according to different criteria, such as alphabetical order or hire date. With querying, you can filter the employee list to show only employees that meet certain criteria, such as those with a specific job title or in a certain location.

active	By including the "active" query parameter in your API request, you can exclude any employees from the results that are no longer employed by the company. This parameter can be useful if you only want to see a list of current employees, without including former employees who are no longer part of the workforce.
skip=n	By including the "skip" query parameter in your API request, you can skip the first n employees in the results list. This parameter can be useful if you only want to see employees beyond the first few entries, allowing you to focus on a particular subset of the employee list.
top=n	By including the "top" query parameter in your API request, you can limit the results to the top n employees in the list. This parameter can be useful if you only want to see the most important or relevant employees, without having to sift through a large number of entries.
search=value	By including the "search" query parameter in your API request, you can filter the employee list by searching for a given value in any of the applicable attributes, such as employee number, name, department, or function. This parameter can be useful if you need to quickly find employees who meet certain criteria, without having to manually search through the entire list.
filter=expression	
By including the "filter" query parameter in your API request, you can filter the results of the request based on a specified condition or set of conditions. The "filter" parameter accepts an expression in the OData Filter Language, which provides a flexible and powerful way to construct filter conditions.

sort=attributes	
By including the "sort" query parameter in your API request, you can sort the employee list based on one or more specified attributes. To use this parameter, you will need to provide a comma-separated list of attribute names that you wish to sort on.

You can also specify a minus prefix to sort the attribute in descending order. For example, if you wanted to sort the employee list by last name in descending order, you would include the parameter "sort=-lastName".

include=contracts	By including the "include" query parameter in your API request, you can choose to include additional information in the search results. Specifically, including the "contracts" value for the "include" parameter will cause the endpoint to also return a list of all the employment contracts associated with the employee(s) in the search results.
GET /v1.0/employees/{nr}
By using this API endpoint, you can retrieve detailed information about a specific employee, using their technical employee number. To use this endpoint, you will need to provide the employee number in the URL path.

Additionally, you can include query parameters to retrieve additional information about the employee. If you include the query parameter "include=contracts", the endpoint will return a list of all the employment contracts associated with the employee. If you include the query parameter "include=documents", the endpoint will return a list of all the documents that are linked to the employee's personnel file.

include=contracts,documents	Include this query parameter to include contracts, documents or both in the search results
GET /v1.0/employees/{nr}/documents
This API endpoint allows you to retrieve all the documents that are linked to a designated employee's personnel file, but not those associated with their employment contracts. To use this endpoint, you will need to provide the employee number in the URL path.

Once the request has been processed, the endpoint will return a list of all the documents that are associated with the employee's personnel file.

POST /v1.0/employees/{nr}/documents
By using this API endpoint, you can add a new document to the personnel file of a designated employee, without associating it with a specific employment contract. To use this endpoint, you will need to provide the employee number in the URL path.

GET /v1.0/employees/{nr}/contracts
This API endpoint allows you to retrieve all the employment contracts associated with a designated employee, using their technical employee number. To use this endpoint, you will need to provide the employee number in the URL path.

include=documents	Include this query parameter to also retrieve the documents that are linked to the employment contracts
GET /v1.0/employees/{nr}/contracts/{nr}
This API endpoint allows you to retrieve a specific employment contract for a designated employee, using their technical employee number and contract number. To use this endpoint, you will need to provide the employee number and the contract number in the URL path.

include=documents	Include this query parameter to also retrieve the documents that are linked to the employment contract
GET /v1.0/employees/{nr}/contracts/{nr}/documents
By using this API endpoint, you can retrieve the documents that are linked to a specific employment contract for a designated employee. To access this endpoint, you will need to provide the employee number and the contract number in the URL path. Once the request has been processed, the endpoint will return a list of documents that are associated with the specified employment contract.

POST /v1.0/employees/{nr}/contracts/{nr}/documents
This API endpoint allows you to add a new document to the personnel file of a specified employee, which will be linked to a particular employment contract. To use this endpoint, you will need to specify the employee number and the contract number in the URL path. Once the document has been added, it will be included in the employee's personnel file, along with any other documents associated with the same employment contract.
