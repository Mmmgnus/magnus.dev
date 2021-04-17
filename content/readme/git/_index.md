---
title: "Git"
date: 2020-05-12T19:48:22+02:00
Intro: What is Git? and how to master it in the terminal.
---

## Undo commits that have not been pushed yet

Okey, so you have fucked up, maybe commit something to the wrong branch. No worries, don't push it.

What you want to do is run the reset command:

{{< terminal >}}
git reset <sha1 of commit>
{{< /terminal >}}

You will **not** lose your changes.