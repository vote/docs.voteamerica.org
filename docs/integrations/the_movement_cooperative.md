---
layout: default
title: The Movement Cooperative
parent: Integrations
nav_order: 3
---

# ActionNetwork

When a user makes use of a VoteAmerica tool embed, we collect their their contact information.  This can be
passed to [ActionNetwork](https://actionnetwork.org) to add the user to your email list and/or trigger an Action to inform targetting or ladder conditions.

## Enabling

Enable the **Enable ActionNetwork Sync** checkbox under **Third Party Integrations** on the
**Tools > Settings** page.  You will need to enter the API Key provided by ActionNetwork.

## Actions

Each VoteAmerica tool will get a new Action, like `VoteAmerica
Register` or `VoteAmerica Absentee`.  Each user of the tool will be
added to your list (if they aren't already a member or haven't already
opted-out), and then associated with the Action.

The Action will also have the following referrer_data:

- ``source`` is the value of the ``?source=`` parameter (or ``voteamerica_{tool}``, if not provided)
- ``website`` is the embed URL
- ``email_referrer`` and ``mobile_message_referrer`` are ActionNetwork parameters that are set if the tool was linked via an ActionNetwork email or SMS campaign.

# Bluelink Lightrail

VoteAmerica's tools integrate with [Bluelink Lightrail](https://bluelink.org/lightrail/)
so you can easily sync your data to Civis/Redshift, BigQuery, NGP VAN, Salesforce, Facebook custom
audiences, and more.

## Enable Bluelink Integration

Enable the **Enable Bluelink Sync** checkbox under **Third Party Integrations** on the
**Tools > Settings** page. Make a note of the VoteAmerica subscriber ID under
**Third Party Integrations**.

Then, sign up for [Bluelink Lightrail](https://bluelink.org/lightrail/). Reach
out to your Bluelink support contact and provide your VoteAmerica subscriber ID
to start syncing your VoteAmerica data.

# TMC

VoteAmerica works with [The Movement Cooperative](https://movementcooperative.org/)
to provide easy syncs of your data to your TMC Civis account. If you are a
TMC member, VoteAmerica and TMC can automatically sync your data to your
Civis account.

## Enable TMC Integration

Enable the **Enable The Movement Cooperative Sync** checkbox under
**Third Party Integrations** on the **Tools > Settings** page. Make a note of
the VoteAmerica subscriber ID under **Third Party Integrations**.

Reach out to your TMC support contact and provide your VoteAmerica subscriber ID
to start syncing your VoteAmerica data.
