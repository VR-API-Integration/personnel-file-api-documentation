---
title: "Dossier API Introduction"
keywords: index introduction
tags: [getting_started, file, api, library]
sidebar: guides_sidebar
permalink: index.html
summary: "High level overview of the Dossier API"
---


The **Dossier API** is an API that can be used to add documents to Personnel File from applications that are not part of Youforce or YouServe. Examples are Multi-Functional Printers (MFP), scanners, workflow systems and other applications that produce documents that need to be added to the Personnel File of employees in Youforce or YouServe.

Most MFP's use software that receives a scanned document and stores it in a folder on a local server, sends it using email or other means of distributing the scanned document. Many providers of MFP's also offer customized solutions to send documents to other applications using plugins. A provider or a third party can use the Dossier API to create a plugin that sends the document to Personnel File in Youforce or YouServe, including customized screens on the MFP to select an employee and a document type and to enter a document title.

The diagram below shows a high level overview of the end-to-end system.

{% include image.html file="dossier_api_diagram.png" alt="Dossier API overview" max-width="800" %}
