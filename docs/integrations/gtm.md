---
layout: default
title: Google Tag Manager
parent: Third-party tracking tools
nav_order: 1
---

# Firing events in Google Tag Manager

[Google Tag Manager (GTM)](https://marketingplatform.google.com/about/tag-manager/) is a system from Google that allows you to manage website tags. If you have GTM installed on your website, you can send the VoteAmericaPlus events to GTM using the following JavaScript snippet.

```js
window.dataLayer = window.dataLayer || [];
window.addEventListener("VoteAmericaEvent", function (evt) {
  dataLayer.push(evt.detail.data);
});
```

Once the events are sent to GTM, you'll need to set up triggers for your tags there. [Google has documentation on that here.](https://support.google.com/tagmanager/answer/6106716?hl=en)

See [JavaScript Events](../../software/events) for more details on the types of events and the data contained in each event.
