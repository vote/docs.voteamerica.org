---
layout: default
title: JavaScript Events
parent: Software
nav_order: 4
---

# JavaScript Events

VoteAmerica+ uses JavaScript event tracking and we pass these events up to the parent window of embeds.

These events are can be consumed by the parent window with a little bit of JavaScript. These events have a type of `VoteAmericaEvent` and can be listened for using the following JavaScript snippet.

```js
window.addEventListener('VoteAmericaEvent', function(evt) {
  console.log(evt); // This can be replaced with any function
});
```

## VoteAmerica+ Events

Here's a list of events provided by VoteAmerica+. Some events have variable parameters, such as a state or url. Those variable parameters are denoted with square brackets, such as `[STATE]`.

### Verify Tool

```json
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

### Register

```json
{
  event: "action-start",
  tool: "register",
  state: "[STATE]", 
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"      
}

{
  event: "action-finish",
  method: "external",
  tool: "register",
  url: "[EXTERNAL URL]",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}

{
  event: "action-finish",
  method: "pdf",
  tool: "register",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"   
}

{
  event: "action-finish",
  method: "pdf-forward",
  tool: "register",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}

{
  event: "action-finish",
  method: "pdf-forward-confirmed",
  tool: "register",
}
```

### Absentee Tool

```json
{
  event: "action-start",
  tool: "absentee",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}

{
  event: "action-finish",
  method: "pdf",
  tool: "absentee",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}

{
  event: "action-finish",
  method: "external",
  tool: "absentee",
  url: "[EXTERNAL LINK]",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}

{
  event: "action-finish",
  method: "external-confirmed",
  tool: "absentee",
  url: "[EXTERNAL LINK]",
  state: "[STATE]",
  first_name: "[FIRST NAME]",
  last_name: "[LAST NAME]",
  email: "[EMAIL]",
  zipcode: "[ZIP CODE]"
}

{
  event: "action-finish",
  method: "fax",
  tool: "absentee",
  state: "[STATE]",
}

{
  event: "action-finish",
  method: "email",
  tool: "absentee",
  state: "[STATE]",
}

{
  event: "action-finish",
  method: "pdf-forward",
  tool: "absentee",
  state: "[STATE]",
}

{
  event: "action-finish",
  method: "pdf-forward-confirmed",
  tool: "absentee",
}

{
  event: "action-restart",
  tool: "absentee",
}
```

### LEO Lookup Tool

```json
{
  event: "action-finish",
  tool: "leo",
  state: "[STATE]",
}
```

### Upcoming Elections Tool

```json
{
  event: "action-finish",
  tool: "upcoming",
  state: "[STATE]",
}
```

### Where To Vote Tool

```json
{
  event: "action-finish",
  tool: "locator",
  state: "[STATE]",
}
```
