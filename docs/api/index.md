---
layout: default
title: API
has_children: true
nav_order: 3
---

# Election Information API

The Election Information API powers the VoteAmerica website and suite of tools.

This API is available as part of the VoteAmerica premium tools. You can [learn more about our premium tools here](https://www.readysetvote.io/).

This data has been gathered and vetted by our research staff, but if you see an error please [report it](https://www.voteamerica.com/report-incorrect-info/).

The API base URL is `https://api.voteamerica.com/v1/`. For example, you can try running `curl https://api.voteamerica.com/v1/election/field/`.

You will need to create an API key. You can do this from your [Ready Set Vote dashboard](https://dashboard.readysetvote.io/manage/).

## GET `/election/field/`

Authentication: none

Returns an array of state information field objects. Each contains a slug, a longer description, and a field format type.

Slugs can be matched to the results in `/state/{state}`. Descriptions are used as headers on VoteAmerica.com

### Field Types

You can find a listing of all of the 90+ Election Information API fields [on our website](https://www.voteamerica.com/election-data-api-fields/).

## GET `/election/data/state/{state}/`

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
