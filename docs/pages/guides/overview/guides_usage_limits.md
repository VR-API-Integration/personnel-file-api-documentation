---
title: Usage Limits
tags: [getting_started, troubleshooting]
keywords: api, library, api policies
last_updated: 2023-08-23
summary: "We apply usage limits to ensure the availability of our services to all parties interacting with Personnel File. These usage limits depend on your subscription."
sidebar: guides_sidebar
permalink: guides_usage_limits.html
folder: guides/overview
topnav: topnav
---

## Policy

The following policies are determined per registered application:

| Quota                                                    |                                                              |
| -------------------------------------------------------- |  --------------------------------------------------------------------- |
| Authentication calls                                     | 400 authentication calls per month                                    |
| Spike arrest policy (max number of API calls per minute) | 100 calls per minute                                                  |

## Spike arrest details

Spike arrest is the way we protect against traffic spikes. Our APIs and backend can handle a certain amount of traffic, and the Spike Arrest policy smooths the traffic to the general amounts.

Spike Arrest’s behaviour differs from what you might expect to see from the literal per minute values.

Our default spike arrest is set to 100pm (100 requests per minute). That does not mean you can do 100 requests inside a 1-second. Spike Arrest smooths the number of full requests in a minute by dividing it into smaller intervals:

**Per-minute** rates get smoothed into full requests allowed in intervals of **seconds**.

For example, 100pm gets smoothed like this:
60 seconds (1 minute) / 100pm = 0.6-second intervals, or 1 request allowed every 0.6 seconds. A second request inside of 0.6 seconds will fail. Also, the 101st request within a minute will fail.

When you exceed the policy, the API will return response code '429 - Too many requests' and you have to wait for the next time window.
