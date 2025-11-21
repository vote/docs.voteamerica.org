---
layout: default
title: Meta (Facebook) pixel
parent: Third-party tracking tools
nav_order: 2
---

# Using Meta/Facebook Pixel Tracking

[Meta Pixel](https://developers.facebook.com/docs/meta-pixel) is a system from Facebook (Meta) that allows you to track conversions. If you have Meta Pixel installed on your website, you can send the VoteAmericaPlus events to Meta Pixel using the following JavaScript snippet.

```js
window.addEventListener('VoteAmericaEvent', function(evt) {
  fbq('track', `${evt.detail.data.tool} - ${evt.detail.data.event}`, evt.detail.data);
});
```

You can read more about [conversion tracking in Meta's documentation](https://developers.facebook.com/docs/meta-pixel/implementation/conversion-tracking)

See [JavaScript Events](../../software/events) for more details on the types of events and the data contained in each event.
