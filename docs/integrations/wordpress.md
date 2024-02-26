---
layout: default
title: WordPress
parent: Integrations
nav_order: 5
---

# Software Embeds and WordPress

WordPress is a widely used content management system for organizations and companies large and small. VoteAmerica+ Tool embeds are compatible with all modern versions of WordPress.

WordPress websites can be configured in different ways, meaning embedding the software can be different website-to-website.

Some themes will allow you to paste the full embed code into the WordPress editor, but many will not.

The most reliable way to embed a tool in WordPress is to add the VoteAmerica+ script using `wp_enqueue_script()`. You can find [documentation here](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) or adding the script tag directly to the theme files.

Once you've done that, you can put the `<div>` tag from the snippet wherever you'd like.


