---
layout: default
title: Register API
parent: API
nav_order: 3
---

# Register API
This API allows third-party partners to complete part of the voter registration
flow via API.

**This API is not available publicly. It is available to select partners who
work closely with us to make sure their usage of the API is compliant**. If
you're interested in this sort of integration, email
[partner@voteamerica.com](mailto:partner@voteamerica.com).

## Overview
The general flow is:
1. The partner sends a `POST` to `/v1/registration/external/request` with the
   basic info on the user.

2. VoteAmerica returns some text to show to the user (this will typically
   contain voter ID requirements, and any specific instructions on how to
   navigate the state online voter registration system), as well as between
   zero and two options for the user to pick from. These options may include
   going to the state's official voter registration website, or going to
   VoteAmerica to print and mail a paper form.

## API Endpoints

### `POST /v1/registration/register/`

Auth: basic auth, API key ID as the username and API key secret as the password

Body: the fields from the first page of register:

```typescript
{
    "title": "Mr",
    "first_name": "John",
    "last_name": "Hancock",
    "address1": "30 Beacon Street",
    "city": "Boston",
    "state": "MA",
    "previous_address1": "133 Franklin St",
    "previous_city": "Quincy",
    "previous_state": "MA",
    "previous_zipcode": "02169",
    "email": "john@hancock.local",
    "year_of_birth": 1937,
    "month_of_birth": 1,
    "day_of_birth": 23,
    "zipcode": "02108",
    "phone": "+16174567890",
    "sms_opt_in": true,
    "sms_opt_in_subscriber": true,
    "us_citizen": true,
    "is_18_or_over": true,
    "state_id_number": "FOUNDER123",
    "party": "Other",
    "race_ethnicity": "White",
    "session_id": "7293d330-3216-439b-aa1a-449c7c458ebe",
    "embed_url": "https://www.greatvoter.com/location/of/embed?secret_data=here",
    "email_referrer": "abcd123",
    "mobile_referrer": "efgh456",
}
```

200 Response format:

```typescript
{
    // the unique identifier for this voter, keep this for future use
    uuid: "dd8404c8-bc12-11ec-8422-0242ac120002"
}
```
