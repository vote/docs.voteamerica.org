---
layout: default
title: API
has_children: true
nav_order: 3
---

# VoteAmerica+ APIs

API keys are only available to VoteAmerica+ customers. 
Please contact [sales@voteamerica.com](mailto:sales@voteamerica.com) to learn more.

## Interactive API Documents

To see query request and response examples, visit our interactive interface here: 
[https://api.voteamerica.com/docs/api/v2](https://api.voteamerica.com/docs/api/v2)

## Civic Data API

If you've ever wanted to build your own Election Center of state-specific data, this is the API for you. 
There are 51 different sets of laws governing elections in the United States 
because we like to make things as complicated as possible.  We've navigated this mess so you don't have to.  
The data in this API powers the VoteAmerica site and is surfaced throughout the VoteAmerica tools.

[Civic Data API fields and descriptions are here](https://www.voteamerica.com/civic-data-api/).

### Versions

Version 2 of the Civic Data API is now available. The remainder of this page describes V2. 
You can find [historic docs for V1 here](/api/v1). 
Our [Upgrade Guide](/api/upgrade_guide) details all the changes and the rationale behind them.

### Using the API

The API base URL is `https://api.voteamerica.com/v2/`. 
For example, you can try running `curl https://api.voteamerica.com/v2/election/field/`.

### Authentication

Some endpoints (indicated below) require an API key. If you are already a VoteAmerica+ customer with an active
subscription to the Civic Data API, you can generate an API key 
[via the VoteAmerica+ Customer Dashboard](https://secure.voteamerica.com/civic-data-api/). 
Please contact [sales@voteamerica.com](mailto:sales@voteamerica.com) to learn more.

For endpoints requiring authentication, use basic auth with your API key ID as the username 
and API key secret as the password.

### GET `/election/field/`

Authentication: none

Returns an array of state information field objects. Each contains a slug, a longer description, and a field format.
Fields using the format `Multi-select` or `Single-select` also include an `options` property that lists the
possible options available for selection. 

(For example: `absentee_request_methods` is a `Multi-select` field that includes
these options: `["email", "fax", "in_person", "mail", "online", "phone"]`. Each state's value for this field will
include a list of the options applicable to the state.)

Slugs can be matched to the results in `/election/data/state/{state}`.

Possible field formats include: `Boolean`, `Date`, `Markdown`, `Multi-select`, `Single-select`, `URL`.

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

Authentication: basic auth ([details](#authentication))

Returns all state information fields for a single state. 
`{state}` should be a 2-letter postal abbreviation, in upper case.

Each item in the `state_information` list has a `field_type` property that maps to 
a slug in the `GET /election/field/` response.

The state's value for a field is returned in 2 different ways:
* `text` always gives a string representation of the value.
* `value` gives the value in a type that varies depending on the field's format. For Boolean-format fields, a 
boolean value is given, and for Multi-select-format fields, a list is given. For all other field formats, the value
is provided as a string.

The `footnote` property is populated when the state's value for a given field has exceptions or 
requires further explanation.

```markdown
{
    "code": string,
    "name": string,
    "state_information": [
        {
            "text": string,
            "field_type": string,
            "value": boolean | list | string,
            "footnotes" string,
            "modified_at": datetime
        }
    ]
}
```

