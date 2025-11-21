---
layout: default
title: Embedded software
nav_order: 3
---

# Embedded software

VoteAmericaPlus software can be embedded in other websites with a short snippet of code.
The software has minimal branding, and the fonts and color scheme should work with any website design.

## Getting started

To start using embedded voter tools, sign up for a free VoteAmericaPlus account at [secure.voteamerica.org/signup/](https://secure.voteamerica.org/signup/).

Once you're logged in to your account, you can find your custom embed codes at [secure.voteamerica.org/embed/](https://secure.voteamerica.org/embed/).
You'll also be able to see counts of the actions driven by your embeds in your dashboard.

If you'd like access to the information gathered via your embeds, you'll need to [upgrade to a paid account](https://secure.voteamerica.org/upgrade/).

## Technical details

The embed code will load our tool asynchronously via Javascript into a div with the class `voteamerica-embed`. 
This will not block rendering of the parent page, and the iframe will check the URL of the parent page for 
[tracking URL arguments](/software/tracking/).

If you have a paid account, the tool will pass JavaScript events to the parent window when users complete actions. 
Find more details on the [JavaScript Events page](/software/events/). 
