---
layout: default
title: Civic Data API
has_children: true
nav_order: 7
---

# VoteAmericaPlus Civic Data API
{: .no_toc }

If you've ever wanted to build your own Election Center of state-specific data, this is the API for you. 
There are 51 different sets of laws governing elections in the United States 
because we like to make things as complicated as possible.  We've navigated this mess so you don't have to.  
The data in this API powers the VoteAmerica site and is surfaced throughout the VoteAmerica tools.

[Civic Data API fields and descriptions are here](https://www.voteamerica.org/civic-data-api/).

API keys are only available to VoteAmericaPlus customers. 
Please contact [sales@voteamerica.org](mailto:sales@voteamerica.org) to learn more.

1. TOC
{:toc}

## Versions

Version 2 of the Civic Data API is now available. The remainder of this page describes V2. 
You can find [historic docs for V1 here](/api/v1). 
Our [Upgrade Guide](/api/upgrade_guide) details all the changes and the rationale behind them.

## Interactive API Documents
{: .no_toc }

To see query request and response examples, visit our interactive interface here: 
[https://api.voteamerica.org/docs/api/v2](https://api.voteamerica.org/docs/api/v2)

## Using the API

The API base URL is `https://api.voteamerica.org/v2/`. 
For example, you can try running `curl https://api.voteamerica.org/v2/election/field/`.

## Authentication

Some endpoints (indicated below) require an API key. If you are already a VoteAmericaPlus customer with an active
subscription to the Civic Data API, you can generate an API key 
[via the VoteAmericaPlus Customer Dashboard](https://secure.voteamerica.org/civic-data-api/). 
Please contact [sales@voteamerica.com](mailto:sales@voteamerica.com) to learn more.

For endpoints requiring authentication, use basic auth with your API key ID as the username 
and API key secret as the password.

## Endpoints

### GET `/election/field/`

**Authentication:** none

**Returns:** An array of state information field objects. 

**Notes:** 

Each state information field object contains a slug, a longer description, and a field format.
Fields using the format `Multi-select` or `Single-select` also include an `options` property that lists the
possible options available for selection. 

(For example: `absentee_request_methods` is a `Multi-select` field that includes
these options: `["email", "fax", "in_person", "mail", "online", "phone"]`. Each state's value for this field will
include a list of the options applicable to the state.)

Slugs can be matched to the results in `/election/data/state/{state}`.

Possible field formats include: `Boolean`, `Date`, `Markdown`, `Multi-select`, `Single-select`, `URL`.

**Response structure:**

```markdown
[
  {
    "slug": string,
    "description": string,
    "field_format": string,
    "options": list (only included for Multi-select and Single-select field formats)
  }
]
```

### GET `/election/data/state/{state}/`

**Authentication:** basic auth ([details](#authentication))

**Parameters:** `{state}` should be a 2-letter postal abbreviation, in upper case.

**Returns:** All state information fields for a single state.

**Notes:** 

Each item in the `state_information` list has a `field_type` property that maps to 
a slug in the `GET /election/field/` response.

The state's value for a field may be returned in a couple different ways:
* `text` always gives a string representation of the value.
* If the field type is `Boolean`, the response will also include a boolean representation called `bool_value`. 
Otherwise, this property won't be present.
* If the field type is `Multi-select`, the response will also include a list representation called 
`multiselect_value`. Otherwise, this property won't be present.

The `footnotes` property is populated when the state's value for a given field has exceptions or 
requires further explanation.

**Response structure:**

```markdown
{
    "code": string,
    "name": string,
    "state_information": [
        {
            "field_type": string,
            "text": string,
            "bool_value": boolean,
            "multiselect_value": list,
            "footnotes" string,
            "modified_at": datetime
        }
    ]
}
```

### GET `/election/override/`

**Authentication:** basic auth ([details](#authentication))

**Returns:** A list of regional overrides, which are cases where regional-level data (usually representing a county) 
overrides state-level data. 

**Notes:** 

In a few cases, specific regions within a state have their own value for a field. 
For example, some cities and counties in Illinois have their own absentee ballot request tool URLs
(represented by the field `gov_tool_absentee_request`). For voters in these regions, the regional-level URL should
be used instead of the state-level URL. 

This endpoint returns a list of all regional overrides. For each, the state name, region name, field slug
and regional-level value is provided.

**Response structure:**

```markdown
[
  {
    "state": string,
    "region": {
      "name": string
    },
    "field": {
      "slug": string
    },
    "value": string
  }
]
```
