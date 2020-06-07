---
title: "Browsersync"
date: 2019-06-24T23:15:51+02:00
draft: false
intro: "[Browsersync](https://browsersync.io/) is a nice tool, that makes it possible to test the site on multiple devices *at the same time!*."
---

## How to use Browsersync

### Install it
{{< terminal >}}
`npm install -g browser-sync`
{{< /terminal >}}

### Static sites
If you’re only using .html files, you’ll need to use the server mode. Browsersync will start a mini-server and provide a URL to view your site.
{{< terminal >}}
`browser-sync start --server --files "css/*.css"`
{{< /terminal >}}

### Dynamic sites
If you’re already running a local server with PHP or similar, you’ll need to use the proxy mode. Browsersync will wrap your vhost with a proxy URL to view your site.

{{< terminal >}}
`browser-sync start --proxy "myproject.dev" --files "css/*.css"`
{{< /terminal >}}

## Links

[Browsersync.io](https://browsersync.io/)
