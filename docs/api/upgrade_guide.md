---
layout: default
title: Upgrading from V1 to V2
parent: API
nav_order: 1
---

# Upgrading from V1 to V2 of the Civic Data API
{: .no_toc }

[Version 2](/api) of the VoteAmerica+ Civic Data API is now available. This guide outlines the changes from 
[Version 1](/api/v1) and their rationale. 

1. TOC
{:toc}

## New features

### Regional overrides

As if 51 different sets of laws governing elections weren't enough, sometimes specific regions within a state
do things differently. For instance, the state of Illinois doesn't have just one URL where people across the state
can request absentee ballots; some cities and counties have their own. 

This is where our new overrides endpoint comes in. It returns a list of override objects, each of which is a case 
where region-level information should override state-level information. For each, the state name, region name, 
name of the field being overridden and region-level value is provided. [See the V2 docs](/api/#get-electionoverride) 
for more information.

* Footnotes
* Multi-select fields
* Naming conventions

## Breaking changes

### Renamed property `description`

### Deleted fields

### Renamed fields

### Consolidated fields