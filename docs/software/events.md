---
layout: default
title: JavaScript events
parent: Data management
nav_order: 3
---

# JavaScript events
{: .no_toc }

VoteAmericaPlus uses JavaScript event tracking, and we pass these events up to the parent window of embeds.

These events can be consumed by the parent window with a bit of JavaScript. These events have a type of `VoteAmericaEvent` and can be listened for using the following JavaScript snippet.

```js
window.addEventListener('VoteAmericaEvent', function(evt) {
  console.log(evt); // This can be replaced with any function
});
```

## VoteAmericaPlus Events
{: .no_toc }

Here's a list of events provided by VoteAmericaPlus tools and their detailed data. You can find this data by accessing the `detail.data` property within the event.

Some events have variable parameters, such as a state or url. Those variable parameters are denoted with square brackets, such as `[STATE]`.

1. TOC
{:toc}

### Absentee Tool

#### action-start event

Fired when the user submits the Absentee tool intake form.

```json-doc
{
  event: "action-start",
  tool: "absentee",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}
```

#### action-finish event

Fired when the user has reached an end point in the Absentee workflow. 

```json-doc
{
  event: "action-finish",
  method: "[METHOD]", // see below for possible options
  tool: "absentee",
  url: "[EXTERNAL LINK]", // only included on events where the user was directed to an external site 
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `external` - The user clicked a link to visit a state-hosted online ballot request website (not available in all states).
* `pdf` - The user received an email with a PDF ballot request form they can print and mail.
* `ineligible-state` - The user was told that online and PDF options are not available in their state. They were provided details for contacting their local election office (applies to Mississippi).
* `leo-referral` - The user was told about unusual rules in their state that may require them to contact their local election office, and they clicked the link to look up the contact details for this office.
* `redirect-to-register`- The user lives in a universal vote-by-mail state (they will automatically receive a ballot in the mail) and were asked whether they needed to update their address permanently or request a one-time ballot. They indicated they needed to update their address permanently and were redirected to the Register tool. (In this situation, an `action-start` event will be fired on the Register action simultaneously.)

#### action-follow-up event

Fired when the user returns to the Absentee flow and takes another action after an `action-finish` has occurred
(ex: Confirming that they successfully requested a ballot on a state website).

```json-doc
{
  event: "action-follow-up",
  method: "[METHOD]", // see below for possible options
  tool: "absentee",
  url: "[EXTERNAL LINK]", // only included on events where the user was directed to an external site 
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `external-confirmed` - After clicking on a link to visit a state ballot request website, the user returned to the flow and confirmed that they successfully requested their absentee ballot.
* `pdf` - After clicking on a link to visit a state ballot request website, the user returned and indicated they wanted to submit their request by mail instead. They received an email with a PDF ballot request form to print and mail.


### FutureVoter Tool

#### action-start event

Fired when the user submits the FutureVoter tool intake form.

```json-doc
{
  event: "action-start",
  tool: "futurevoter",
  state: "[STATE]", 
  first_name: "[FIRST NAME]",
  zipcode: "[ZIP CODE]"      
}
```

#### action-finish event

Fired when the user has reached an end point in the FutureVoter workflow. 

```json-doc
{
  event: "action-finish",
  method: "[METHOD]", // see below for possible options
  tool: "futurevoter",
  url: "[EXTERNAL URL]", // only included on events where the user was directed to an external site 
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  zipcode: "[ZIP CODE]"
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `external` - The user clicked a link to visit a state-hosted online voter registration website (not available in all states).
* `pdf` - The user received an email with a PDF registration form they can print and mail.
* `ineligible-state` - The user lives in a state where online and PDF registration are not supported. They received details about what to do next.
  * Ex: North Dakota does not have voter registration, so the user was told that no action is required.
  * Ex: New Hampshire prefers that people register in person, so the user received details about how to register on Election Day or contact their local election office
* `redirect-to-register` - The user is over 18, so they were redirected to the Register tool. (In this situation, an `action-start` event will be fired on the Register action simultaneously.)

#### action-follow-up event

Fired when the user returns to the flow and takes another action after an `action-finish` has occurred
(ex: Confirming that they successfully registered on a state online voter registration website).

```json-doc
{
  event: "action-follow-up",
  method: "[METHOD]", // see below for possible options
  tool: "futurevoter",
  url: "[EXTERNAL LINK]", // only included on events where the user was directed to an external site 
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  zipcode: "[ZIP CODE]"
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `external-confirmed` - After clicking on a link to visit a state voter registration website, the user returned to the flow and confirmed that they successfully registered.
* `pdf` - After clicking on a link to visit a state voter registration website, the user returned and indicated they wanted to register by mail instead. They received an email with a PDF registration form to print and mail.

### Permanent Absentee Voter (PAV) Tool

#### action-start event

Fired when the user submits the Permanent Absentee Voter tool intake form.

```json-doc
{
  event: "action-start",
  tool: "pav",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"    
}
```

#### action-finish event

Fired when the user has reached an end point in the Permanent Absentee Voter workflow. 

```json-doc
{
  event: "action-finish",
  method: "[METHOD]", // see below for possible options
  tool: "pav",
  url: "[EXTERNAL LINK]", // only included on events where the user was directed to an external site 
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `external` - The user clicked a link to visit a state-hosted online permanent absentee voter signup website (not available in all states).
* `pdf` - The user received an email with a PDF permanent absentee voter signup form they can print and mail.
* `ineligible-state` - The user was told that their state does not offer a permanent absentee voting program.

#### action-follow-up event

Fired when the user returns to the Permanent Absentee Voter flow and takes another action after an `action-finish` has occurred.

```json-doc
{
  event: "action-follow-up",
  method: "[METHOD]", // see below for possible options
  tool: "pav",
  url: "[EXTERNAL LINK]", // only included on events where the user was directed to an external site 
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `external-confirmed` - After clicking on a link to visit a state permanent absentee voter signup website, the user returned to the flow and confirmed that they successfully submitted their request.
* `pdf` - After clicking on a link to visit a state permanent absentee voter signup website, the user returned and indicated they wanted to submit their request by mail instead. They received an email with a PDF permanent absentee voter signup form to print and mail.
* `redirect-to-absentee` - After being told that their state doesn't offer a permanent absentee voting program, the user clicked on the option to request a one-time ballot and was redirected to the Absentee tool. (In this situation, an `action-start` event will be fired on the Absentee action simultaneously.)


### Pledge Tool

#### action-start event

Fired when the user submits the Pledge tool intake form.

```json-doc
{
  event: "action-start",
  tool: "pledge",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"    
}
```

#### action-finish event

Fired when the user receives confirmation that they have pledged to vote and subscribed to election reminders (we expect this to immediately follow form submission).

```json-doc
{
  event: "action-finish",
  tool: "pledge",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"    
}
```


### Register Tool

#### action-start event

Fired when the user submits the Register tool intake form.

```json-doc
{
  event: "action-start",
  tool: "register",
  state: "[STATE]", 
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"      
}
```

#### action-finish event

Fired when the user has reached an end point in the Register workflow. 

```json-doc
{
  event: "action-finish",
  method: "[METHOD]", // see below for possible options
  tool: "register",
  url: "[EXTERNAL URL]", // only included on events where the user was directed to an external site 
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `external` - The user clicked a link to visit a state-hosted online voter registration website (not available in all states).
* `pdf` - The user received an email with a PDF registration form they can print and mail.
* `ineligible-state` - The user lives in a state where online and PDF registration are not supported. They received details about what to do next.
  * Ex: North Dakota does not have voter registration, so the user was told that no action is required.
  * Ex: New Hampshire prefers that people register in person, so the user received details about how to register on Election Day or contact their local election office
* `redirect-to-future-voter` - The user is too young to register to vote, so they were redirected to the FutureVoter tool. (In this situation, an `action-start` event will be fired on the FutureVoter action simultaneously.)

#### action-follow-up event

Fired when the user returns to the flow and takes another action after an `action-finish` has occurred
(ex: Confirming that they successfully registered on a state online voter registration website).

```json-doc
{
  event: "action-follow-up",
  method: "[METHOD]", // see below for possible options
  tool: "register",
  url: "[EXTERNAL LINK]", // only included on events where the user was directed to an external site 
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `external-confirmed` - After clicking on a link to visit a state voter registration website, the user returned to the flow and confirmed that they successfully registered.
* `pdf` - After clicking on a link to visit a state voter registration website, the user returned and indicated they wanted to register by mail instead. They received an email with a PDF registration form to print and mail.

### Reminders Tool

#### action-start event

Fired when the user submits the Reminders tool intake form.

```json-doc
{
  event: "action-start",
  tool: "remind",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"    
}
```

#### action-finish event

Fired when the user receives confirmation that they have been subscribed to election reminders (we expect this to immediately follow form submission).

```json-doc
{
  event: "action-finish",
  tool: "remind",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"    
}
```

### Calendar Tool

#### action-start event

Fired when the user submits the Calendar tool intake form.

```json-doc
{
  event: "action-start",
  tool: "upcoming",
  state: "[STATE]",
  zipcode: "[ZIP CODE]"    
}
```

#### action-finish event

Fired when Calendar results are delivered to the user (we expect this to immediately follow form submission).

```json-doc
{
  event: "action-finish",
  tool: "upcoming",
  state: "[STATE]",
  zipcode: "[ZIP CODE]",
  method: "[METHOD]" // see below for possible options
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `point` - The user's address was successfully geocoded. The calendar results are based on the person's geolocation.
* `state` - We were unable to geocode the user's address. The calendar results are based only on the person's state.


### Verify Tool

#### action-start event

Fired when the user submits the Verify tool intake form.

```json-doc
{
  event: "action-start",
  tool: "verify",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"    
}
```

#### action-finish event

Fired when Verify results are delivered to the user (we expect this to immediately follow form submission).

```json-doc
{
  event: "action-finish",
  tool: "verify",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"    
}
```

#### action-follow-up event

Fired when, after seeing results indicating they might not be registered, the user takes an additional action.

```json-doc
{
  event: "action-follow-up",
  tool: "verify",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]",
  method: "[METHOD]" // see below for possible options    
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `redirect-to-register` - The user clicked to register to vote and was redirected into the Register flow. (In this situation, an `action-start` event will be fired on the Register action simultaneously.)
* `external` - The user clicked to check their registration status directly via a state website. 
* `retry` - The user clicked to try again with updated information and was redirected back to the Verify intake form.

### Where To Vote Tool

#### action-start event

Fired when the user submits the Where to Vote tool intake form.

```json-doc
{
  event: "action-start",
  tool: "locator",
  state: "[STATE]",
  email: "[EMAIL]",
}
```

#### action-finish event

Fired when Where to Vote results are delivered to the user (we expect this to immediately follow form submission).

```json-doc
{
  event: "action-finish",
  tool: "locator",
  state: "[STATE]",
  email: "[EMAIL]",
  method: "[METHOD]" // see below for possible options
}
```

The `method` property will provide more details about what took place. Possible `method` options include:
* `google-civic` - The Where to Vote results are from the Google Civic API.
* `external` - No polling place data was available from the Google Civic API for the user's address. Instead, the user was directed to a state-hosted polling place lookup tool.
