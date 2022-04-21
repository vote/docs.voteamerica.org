---
layout: default
title: Election Information API
nav_order: 3
---

# Election Information API

The Election Information It contains approximately 100 points of data per state.  This information is surfaced on the VoteAmerica website and within varius tool workflows. You can see all of the fields currently available on this page: https://www.voteamerica.com/election-data-api-fields/

We license access to this data on both a monthly an annual basis. If you are interested in an API key, please contact sales@voteamerica.com

This data has been gathered and vetted by our research staff, but if you see an error please [report it](https://www.voteamerica.com/report-incorrect-info/).

The API base URL is `https://api.voteamerica.com/v1/`. For example, you can try running `curl https://api.voteamerica.com/v1/election/field/`.


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
