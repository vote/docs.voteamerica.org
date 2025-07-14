---
layout: default
title: ActionNetwork
parent: Data syncs
nav_order: 1
---

# ActionNetwork

When a user makes use of a VoteAmerica+ software embed, we collect their contact information.  This can be
passed to [ActionNetwork](https://actionnetwork.org) to add the user to your email list and/or trigger an Action to inform targeting or ladder conditions.

## Enabling

Enable the **Enable ActionNetwork Sync** checkbox under **Third Party Integrations** on the
**Tools > Settings** page.  You will need to enter the API Key provided by ActionNetwork.

## Actions

Each VoteAmerica+ tool will get a new Action, like `VoteAmerica
Register` or `VoteAmerica Absentee`.  Each user of the tool will be
added to your list (if they aren't already a member or haven't already
opted-out), and then associated with the Action.

The Action will also have the following referrer_data:

- ``source`` is the value of the ``?source=`` parameter (or ``voteamerica_{tool}``, if not provided)
- ``website`` is the embed URL
- ``email_referrer`` and ``mobile_message_referrer`` are ActionNetwork parameters that are set if the tool was linked via an ActionNetwork email or SMS campaign.


