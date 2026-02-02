---
layout: default
title: Action Network
parent: Data syncs
nav_order: 1
---

# Action Network

When a user submits a form on your instance of the VoteAmericaPlus tools, we collect their contact information.  This can be
passed to [Action Network](https://actionnetwork.org) to add the user to your email list and/or trigger an Action to inform targeting or ladder conditions.

## Enabling

1. Set up your Action Network account.
2. Generate an API from the API & Sync page in Action Network. [Learn more in the Action Network docs](https://actionnetwork.org/docs/).
Be sure to copy the secret API key, as you will need it to complete the process.
3. In the VoteAmericaPlus dashboard, navigate to the [Company Settings](https://secure.voteamerica.org/settings/) page and scroll to "Third-party integrations".
4. Check the box "Enable Action Network Sync", then paste your API key into the provided field. Click "Save".

## Actions

Each VoteAmericaPlus tool will get a new Action, like `VoteAmerica
Register` or `VoteAmerica Absentee`.  Each user of the tool will be
added to your list (if they aren't already a member or haven't already
opted-out), and then associated with the Action.

The Action will also have the following referrer_data:

- ``source`` is the value of the ``?source=`` parameter (or ``voteamerica_{tool}``, if not provided)
- ``website`` is the embed URL
- ``email_referrer`` and ``mobile_message_referrer`` are ActionNetwork parameters that are set if the tool was linked via an ActionNetwork email or SMS campaign.


