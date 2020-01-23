---
title: "IOS Development"
date: 2020-01-20T23:20:06+02:00
draft: true
---

# IOS Development

## Network Link Conditioner
When you want to simulate bad internet connection, Network Link Conditioner is a great tool.

https://nshipster.com/network-link-conditioner/

### From the article regarding an issue in OSX 10.14:

"When you first install Network Link Conditioner on macOS 10.14, everything works as expected. But if you close and reopen System Preferences, the preference pane no longer appears, and attempting to reinstall results in the following error message:

[ You can't install the 'Network Link Conditioner' preferences. ]

As a workaround, you can move the preference pane from your user PreferencePanes directory to the system-level directory by entering the following command in Terminal.app (you’ll be prompted for your password):

`$ sudo mv ~/Library/PreferencePanes/Network\ Link\ Conditioner.prefPane /Library/PreferencePanes/`

Once you’ve done this, Network Link Conditioner will appear the next time you open System Preferences.

