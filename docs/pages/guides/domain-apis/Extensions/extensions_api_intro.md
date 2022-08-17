---
title: Extensions API
tags: [extensions, api]
keywords: extensions, api
last_updated: 08/12/2022
sidebar: guides_sidebar
permalink: extensions_api_intro.html
folder: guides/domain-apis
topnav: topnav
---
<span class="label label-danger">CONCEPT</span>

The purpose of this API is to add addtional fields to an existing domain API. With this API customers can customize the integration with their external system, like their IAM or learning system Customization means adding custom fields to the domain api on Person and Employment entity.

Extensions are always liked to a specific Application. Adding extension needs to be done by Visma Raet as part of the onboard of an application for specific customer.

## Processes
The following processes can be supported with the domain API:
- Get all the exenstions for the persons by an application
- Get all the exenstions for the Employment  by an application
## Domain model
With different endpoint, the extension API will support the following additional  model

{% include image.html file="extensions.png" alt="Extensions model " %}
