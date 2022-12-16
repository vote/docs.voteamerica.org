---
layout: default
title: Source Tracking
parent: Toolset
nav_order: 3
---

# Tracking URL Arguments

All standard UTM parameters, as well as `source`, can be used to track campaign performance, differentiate traffic from different sources, and determine conversion events.

These can be set in the URL of the page where the tool is embedded, or passed in as a data-attribute on the embed itself.

|Parameter|Purpose|Example|
|---|---|---|
utm_source|Identifies which site sent the traffic.|utm_source=example.org
utm_medium|Identifies what type of link was used, such as cost per click, social media ad, or email.|utm_medium=facebook
utm_campaign|Identifies a specific product promotion or strategic campaign.|utm_campaign=vbm_xx_1
utm_term|Identifies search terms.|utm_term=vote+by+mail
utm_content|Identifies what specifically was clicked to bring the user to the site. Often used for A/B testing and targeted ads.|utm_content=test_a or utm_content=test_b
source|A generic string issued automatically by some email service providers|source=my_source_here


## Defaults and Overrides

In addition to allowing these parameters, we allow setting default and override UTM attributes within the embed code.

**Default attributes:**

```
data-default-Source
data-default-Utm-Campaign
data-default-Utm-Source
data-default-Utm-Medium
data-default-Utm-Term
data-default-Utm-Content
```

**Override attributes:**

```
data-override-Source
data-override-Utm-Campaign
data-override-Utm-Source
data-override-Utm-Medium
data-override-Utm-Term
data-override-Utm-Content
```

