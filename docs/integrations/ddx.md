---
layout: default
title: DDx
parent: Data syncs
nav_order: 3
---

# DDx

You can sync information between VoteAmericaPlus and other tools you use for organizing and outreach 
via the [DDx Interactions API](https://apidocs.demexchange.com/docs/interactions-api-overview).

The Interactions API involves 3 different actors:
* **Data owner** - That's you. You own the data collected via your instance of VoteAmericaPlus tools.
* **Data source** - That's us. VoteAmericaPlus is the data source that collects information from users via your tools.
* **Data destination** - That's the third-party tool you want to sync data to. 
Contact DDx at [api@demexchange.com](mailto:api@demexchange.com) to learn about supported data destinations.

## Enabling

1. Set up your DDx account. (Contact [api@demexchange.com](mailto:api@demexchange.com) for support.)
2. Generate a DDx API key that authorizes VoteAmericaPlus to push interactions to your DDx account. 
When prompted to select a data source, choose `VoteAmerica-to-MIG`. [Learn more in the DDx docs](https://apidocs.demexchange.com/docs/detailed-guide-api-key-creation).
Be sure to copy the secret API key, as you will need it to complete the process.
3. In the VoteAmericaPlus dashboard, navigate to the [Company Settings](https://secure.voteamerica.org/settings/) page and scroll to "Third-party integrations".
4. Check the box "Enable DDx Sync", then paste your DDx API key and organization name into the provided fields. Click "Save".

## Interactions

Each time a user submits a form on your instance of the VoteAmericaPlus tools, VoteAmericaPlus will push an "interaction". 
The interaction will have a method of `web_interaction` and will include details such as:
* The user's email address
* The user's state
* The URL where the form was submitted
* The type of form submitted (e.g. `verify`, `absentee`, `register`, etc.)

This interaction data can then be forwarded to any data destinations you configure on your API key.