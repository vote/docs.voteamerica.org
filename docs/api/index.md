---
layout: default
title: API
has_children: false
nav_order: 3
---

# VoteAmerica+ APIs

API keys are only available to VoteAmerica+ customers. Please contact [sales@voteamerica.com](mailto:sales@voteamerica.com) to learn more.

## Interactive API Documents
Our API docs are currently evolving, but you can get examples, and an interactive interface here: [https://api.voteamerica.com/docs/api/](https://api.voteamerica.com/docs/api/)

## Civic Data API

If you've ever wanted to build your own Election Center of state-specific data, this is the API for you. There are 51 different sets of laws governing elections in the United States because we like to make things as complicated as possible.  We've navigated this mess so you don't have to.  The data in this API powers the VoteAmerica site, and is surfaced throughout the VoteAmerica tools.

[Civic Data API fields and descriptions are here](https://www.voteamerica.com/civic-data-api/).

### Using the API

The API base URL is `https://api.voteamerica.com/v1/`. For example, you can try running `curl https://api.voteamerica.com/v1/election/field/`.


### GET `/election/field/`

Authentication: none

Returns an array of state information field objects. Each contains a slug, a longer description, and a field format type.

Slugs can be matched to the results in `/state/{state}`. Descriptions are used as headers on VoteAmerica.com


### GET `/election/data/state/{state}/`

Auth: basic auth, API key ID as the username and API key secret as the password

Returns all elections information fields for a single state. `{state}` should be a 2-letter postal abbreviation, in upper case.

```json
{
    "code": string,
    "name": string,
    "state_information": [
        {
            "text": string,
            "field_type": string,
            "modified_at": datetime
        }
    ]
}
```

