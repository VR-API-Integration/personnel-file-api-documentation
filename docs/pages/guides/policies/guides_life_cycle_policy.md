---
title: Life Cycle Policy
tags: [getting_started, troubleshooting]
keywords: api, library, api policies
last_updated: Jan 5, 2022
summary: "We aim to provide you with a policy for releases and support for older versions for a consistent and predictable experience.You can also find this information in the Service Level Agreement"
sidebar: guides_sidebar
permalink: guides_life_cycle_policy.html
folder: guides/policies
topnav: topnav
---

## Different types of changes

The life cycle of any API products has dependencies on underlying products. Changes in those products may require changes to the API to support it. We distinguish between breaking changes and non-breaking changes. A breaking change is one that breaks the contract an API consumer depends on, either by a change in structure, behavior or semantics. The release and support strategy makes a clear distinction in how these are managed.

## Major releases

At times Raet may need to make larger changes to the API. Reasons may be changes to legal requirements, adding a large new feature to the API or an change in other products the API depends on. In these cases Raet may create a new major release of the API. We strive to also keep major releases backward compatible as much as possible but this may not always be possible. In case of breaking changes In general Raet aims to have a maximum of one major release per year.

Each major release will be supported for at least 24 months after releasing the next major version.

As a client to our API you will have to adjust your software to follow the major releases of our API as they will impact your integration. You must update your software to support the new API version as older API versions will be decommissioned following the policy as outlined above.

## Minor releases

A minor release will never contain breaking changes, the are used to deliver incremental changes. Minor versions will not be visible in the path of the API. Raet can install minor updates in the standard release windows or as part of a hotfix and will communicate the changes as part of the release notes. Since this does not impact any existing functionality, we do not provide side-by-side support for multiple minor versions of the same major version: a minor upgrade just replaces the previous version.

As a consumer of the API it is up to you to decide if you start using the newly available features.

## Announcing major releases

Each release of a major API version will be accompanied by communication about the support lifecycle of the current version in the release notes.

When approaching the sunset-date for an API product, we will actively reach out to inform any customers still using it:

|Communication|When|Where|Recipient|
|--------|---------|--------|---------|
|Announcement|At the release of the new major version. Includes the date of decommissioning the previous version.|Developers & Visma Community|All recipients & File API contact persons|
|1st notification|6 months prior to decommissioning|Developers & Visma Community|File API contact persons|
|2nd notification|3 months prior to decommissioning|Developers & Visma Community|File API contact persons|
|3rd notification|1 months prior to decommissioning|Developers & Visma Community|File API contact persons|
