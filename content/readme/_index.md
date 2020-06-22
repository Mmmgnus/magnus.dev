---
title: "readme"
date: 2019-06-17T23:20:06+02:00
draft: false
intro: "My collection of personal notes about my development journey in code and life; mostly in code."
---

This is not a log, blog or anything like that. This is only a place for me to store everything I have in my mind so I don't forget important things. Things like:

* What is the best way to implement SVG icons on a website?
* How do you create components in a modular way that is reusable?
* What is the short-commands I use in all my apps and tools?
* How do I write readable code that doesn't smell?
* How do you write good documentations?

## The structure of this readme
*Sorry*, but this collection of knowledges is not well structured, maybe some day in the future but not right now. But I try to follow some structure and guidelines.

### Guidelines

#### Don't think to much about the structure
The most important is to write things down, if I don't know where I should put a piece of information or knowledge, just add it directly under [/readme]({{< ref "/readme" >}}). 

#### Links
Links are stored by topic, You find Javascript links under [/javascript]({{< ref "/readme/javascript" >}}), links about something related to React under [/javascript/react](/readme/javascript/react). If there is no page on the topic, the page should be created or the link should be stored in /links.

#### Problems & solutions
My goal is to log all my problem and what the solution was. Like links they are documented on the corresponding topic under the headline "Issues and solutions" or under a subpage with the same name listing all problems.

### Visual & typography conventions

#### Marked text
Text that is {{<mark>}}marked with a yellow background is text that I think is very important or interesting to me{{</mark>}}. Usually after a second read some text may be marked.

#### Code
Code inlined in text paragraph will look like `this`.

#### Terminal input
Inputs that should be done in a terminal.
{{< terminal >}}
  mkdir my-project-name
{{< /terminal >}}

#### Info block
Infoboxes for information that can be expanded and show more content.
{{< info-box content="It’s possible to open Android Studio from the terminal with the command `android-studio`.">}}
  {{< terminal >}}
    mkdir my-project-name
  {{< /terminal >}}
{{< /info-box >}}

#### Error block
When I want to document any issue or problems on the way, I will put that information into one of these "Issue and solution" block.
{{< error type="terminal">}}
  {{< terminal >}}
    mkdir my-project-name
  {{< /terminal >}}

  {{< error-content >}}
  This error has something to do with a missing import. After some googling I found out that the version I had, `2.5.x` is not supported.

  __Solution:__ Upgrade to version  `3.x.x`.
  {{</ error-content>}}
{{< /error >}}

#### Blockquote
Blockquotes for when I quote someone.
{{< blockquote caption="Magnus Fredlundh, [magnus.dev](http://magnus.dev)" >}}
  My collection of personal notes about my development journey in code and life; mostly in code.
{{</ blockquote >}}

#### Checklist
Checklist like todos will be represented as a list with checkboxes.
{{< checklist >}}
  {{< item checked >}}A todo list item that is done!{{</ item>}}
  {{< item >}}A todo list item that is __not__ done!{{</ item >}}
{{</ checklist >}}